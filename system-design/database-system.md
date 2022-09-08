# Database System

In our project, the implementation of multiple databases is essential to collect and manage data in a systematic way.

First, all the information regarding users must be stored and updated in case of changes. Users’ data, identified by a user ID, will be automatically accessed by the system through SQL queries as soon as they are needed for the emergency progress system.

Then, the registered AEDs must be stored indicating the precise location (expressed using geographical coordinates), the name of the place and all
the information regarding their availability.

Finally, data about the emergency will be stored in a database that is
connected to the emergency micro-service. The system will attribute an ID
to each emergency and will store the following data:

- Coordinates of the emergency.
- List of first responders who received the alert (specifying whether they
accepted or declined it).
- List of AEDs located near the emergency.
