# Emergency Communication Center Functioning

This section explains more in details the role that the Emergency Communications System has in triggering the HeartBeat emergency system.

As we saw before, the emergency management system is triggered by the assignment of the *code blue* to an emergency.
This code is manually assigned by the ECC operator once he/she obtained all the relevant information about the emergency.

When this happens, the HeartBeat emergency management system will receive the following data:

```json
[
    {
        "emergencyId": "0001",
        "time": "15:36",
        "latitude": "67",
        "longitude": "20",
        "reference": "Bank"
    }
]

```
Each emergency that triggers the HeartBeat emergency management system, is assigned to a unique identifier (*emergencyId*) and data about time, position and reference point are stored.

The position, expressed with coordinates, will be used by the system to identify First Resopnders thar located nearby the emergency site.

[This simple python program](https://github.com/HeartBeat-SE/ECC-Software) simulates this process and produces the following output:

![](python-output.jpg)