# Back-End Development

The back-end refers to the parts of the application that allow it to operate and that cannot be accessed by users. 

We identified three micro-services that communicate with each other and with the mobile application through REST APIs.

## Account Service

The first micro-service regards all the operations concerning users’ accounts. More in details, the tasks performed by the **account-service** include:

1. Communication with the accounts’ database through SQL queries to
insert, update and delete accounts.
2. Identification of the suitable first responders on the basis of the location of the emergency.
3. Creation and management of the notification alerts sent to users.

## AED Service

Then, the operations regarding AEDs locations are in charge of the **AED-service**. 
In particular, the tasks performed by this micro-service include:

1. Communication with the AEDs’ database through SQL queries to insert, update and delete AEDs.
2. Identification of the AEDs located near the emergency.

## Emergency Service

The last micro-service that is part of the back-end development is the **emergency-service**. 
This service communicates with the other two services through REST APIs, as we saw in the example above, and with the emergency database with SQL queries. 
The tasks performed by the emergency-service, include:

1. Elaboration of the data received by the Emergency Communications Center and emergency database update.
2. Sharing of the emergency data to the other micro-services and the user app.
3. Sharing with the Emergency Communications Center of the data about first responders who accepted the alert.

## API Design between account-service and AED service

```java
app.get("/", (req, res) => { 
	res.send("This is an API between users and AED locations") 
})

app.get('/users', (req, res) => { 
    let dto = []
    for(user of userModel.getAllUsers()){
        let userDto = convertToUserDto(user)
        dto.push(userDto)
    }

    res.json(dto)
})

app.post("/users", (req, res) => { 
	try {
		userModel.registerNewUser(req.body.userId, req.body.name, req.body.city) 
		res.json(userModel.getUserById(req.body.userId))
	} catch (error){
		res.status(400).json({ error });
	}	
})

app.get('/locations', (req, res) => {
    res.json(locations)
})

app.get('/locations/:id/users', (req, res) => {
    let dto = userModel
        .getAllUsers() 
        .filter(u => u.locations.includes(req.params.id)) 
        .map(convertToUserDto)
    res.json(dto)
})
```

In the script showed above, the design of the APIs that allow the communication between these two micro-services is displayed. 
Here we can see some examples of ’get’ and ’post’ requests on users’ accounts, as well as some ’get’ requests on the AED-service.
