# REST API example

This repository contains code demonstrating Rest API with **GET, POST, PATCH, DELETE** requests samples

(&#61affe;) GET request to get all subscribers
```shell script
$ http://localhost:3002/subscribers/
```

```javascript
router.get('/', async (req, res) => {
    try {
        const subscribers = await Subscriber.find();
        res.json(subscribers)
    } catch (err) {
        res.status(500).json({message: err.message})
    }
});
```

## How to start the project
- Install [MongoDB](http://www.codebind.com/mongodb/install-mongodb-mac-os-x/)
- Run it locally `$ brew services start mongodb-community`
- Lunch server `$ yarn start`
