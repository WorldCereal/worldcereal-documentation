
# openEO based processing

This section explains advanced usage of the processing APIs. It explains how to work with Python and HTTP REST based APIs 
to run WorldCereal processing. This is meant for developers looking to integrate these workflows into their own applications.

The WorldCereal system makes use of the Copernicus Dataspace Ecosystem openEO API.
This use of this is fully documented on the [CDSE website](https://documentation.dataspace.copernicus.eu/APIs/openEO/openEO.html).

We refer to this documentation for more advanced questions and for getting a basic understanding of openEO, but we also 
include concrete examples on this page, to avoid learning the full openEO API, which is quite extensive.

More specifically, WorldCereal workflows are offered as openEO [user defined processes](https://openeo.org/documentation/1.0/developers/api/reference.html#tag/User-Defined-Processes), that should be invoked via
[batch jobs](https://openeo.org/documentation/1.0/developers/api/reference.html#tag/Batch-Jobs).

## Client libraries

OpenEO provides client libraries to support the creation and execution of JavaScript, Python and R services. The full client libraries documentation is available on the official OpenEO support pages:
* [JavaScript](https://openeo.org/documentation/1.0/javascript/)
* [Python](https://openeo.org/documentation/1.0/python/)
* [R](https://openeo.org/documentation/1.0/r/ )

The following example shows a code sample on how to execute a WorldCereal workflow through the OpenEO Python Client.

```python
import openeo

# Setup parameters
aoi = {
    "type": "Polygon",
    "coordinates": [
        [
            [
                5.179324150085449,
                51.2498689148547
            ],
            [
                5.178744792938232,
                51.24672597710759
            ],
            [
                5.185289382934569,
                51.24504696935156
            ],
            [
                5.18676996231079,
                51.245342479161295
            ],
            [
                5.187370777130127,
                51.24918393390799
            ],
            [
                5.179324150085449,
                51.2498689148547
            ]
        ]
    ]
}
date = '2020-06-01'

# Setup connection with OpenEO
eoconn = openeo.connect("openeofed.dataspace.copernicus.eu").authenticate_oidc()

# Create a processing graph from the worldcereal-inference process using an active openEO connection
cropmap = eoconn.datacube_from_process("worldcereal_inference", namespace="https://github.com/ESA-APEx/apex_algorithms/raw/main/openeo_udp/worldcereal_inference.json", bbox=aoi)

# Execute the OpenEO request as a batch job
cropmap_job = cropmap.send_job()
cropmap_job.start_and_wait().get_results()
```

Once the job has started, you can use the interface available at [https://openeo.dataspace.copernicus.eu](https://openeo.dataspace.copernicus.eu)
to monitor it, or use the Python API.

## REST API

OpenEO provides a fully documented REST API. The API can also be used to integrate WorldCereal jobs into your application
if the client libraries are not suitable. The documentation is available at:

| OpenEO |
|---|
| https://openeo.org/documentation/1.0/developers/api/reference.html |

The following example showcases how to use the OpenEO API to execute a request for a WorldCereal service:

```curl
POST /openeo/1.2/jobs HTTP/1.1
Host: openeo.dataspace.copernicus.eu
Content-Type: application/json
Authorization: Bearer basic//basic.cHJvag==
Content-Length: 4587
{
    "title": "Your custom WorldCereal job",
    "process": {
        "id": "cropmap",
        "process_graph": {
            "biopar1": {
                "process_id": "worldcereal_inference",
                "namespace": "https://github.com/ESA-APEx/apex_algorithms/raw/main/openeo_udp/worldcereal_inference.json",
                "arguments": {
                    "bbox": {
                        "west": 5.15183687210083,
                        "east": 5.153381824493408,
                        "south": 51.18192559252128,
                        "north": 51.18469636040683,
                        "crs": "EPSG:4326"
                    }
                },
                "result": true
            }
        }
    },
    "driver-memory": "4g",
    "executor-memoryOverhead": "4g",
    "udf-dependency-archives": [
        "https://artifactory.vgt.vito.be/artifactory/auxdata-public/openeo/onnx_dependencies_1.16.3.zip#onnx_deps"
    ]
}
```

The response of this call will be a json object containing an 'id' property.
This property is the job id that you can use in the subsequent call to [start the job](https://openeo.org/documentation/1.0/developers/api/reference.html#tag/Batch-Jobs/operation/start-job):

```curl
POST /openeo/1.2/jobs/{job_id}/results HTTP/1.1
Host: openeo.dataspace.copernicus.eu
Authorization: Bearer basic//basic.cHJvag==
Content-Length: 0

```

This call will return 202 if successfull. Now you can use other parts of the API to monitor the job,
request logs, result metadata or data itself.

