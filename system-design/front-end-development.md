# Front-End Development

Front-end development refers to the client side of the system with which users can interact directly. For HeartBeat, users have at disposal both a mobile app and a web portal:

The **mobile app** represents the main interface for users as some operations need direct access to active localization, camera or the calling system. 
While the **web portal** only constitutes an alternative means by which users can update their profiles.

The user app communicates with the micro-services through REST APIs in order to transfer data from users to services and vice versa. In particular, its tasks include:

1. Users’ data entry and update.
2. AEDs’ data entry and update.
3. Display of the notification alert and sharing of the data of users who accept it.
4. Display of AEDs and communication with the mapping platform.
