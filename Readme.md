# REST API example

This repository contains code demonstrating Rest API with **GET, POST, PATCH, DELETE** requests samples

![#61affe](https://placehold.it/15/61affe/000000?text=+) **GET** _request to get all subscribers_

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

![#61affe](https://placehold.it/15/61affe/000000?text=+) **GET** _request to get subscriber by `/id`_

```shell script
$ http://localhost:3002/subscribers/5e5fcff1dc53dec90f09512d
```

```javascript
router.get('/:id', getSubscriber, (req, res) => {
    res.json(res.subscriber)
});
```

![#49cc90](https://placehold.it/15/49cc90/000000?text=+) **POST** _request to create one subscriber by `/id`_

```shell script
POST http://localhost:3002/subscribers
Content-Type: application/json

{
  "name": "Amazing Person",
  "subscribedToChannel": "Web Dev test"
}
```

```javascript
router.post('/', async (req, res) => {
    const subscriber = new Subscriber({
        name: req.body.name,
        subscribedToChannel: req.body.subscribedToChannel
    });
    try {
        const newSubscriber = await subscriber.save();
        res.status(201).json(newSubscriber)
    } catch (err) {
        res.status(400).json({message: err.message})
    }
});
```

![#49cc90](https://placehold.it/15/49cc90/000000?text=+) **UPDATE** _request to update one subscriber by `/id`_

```shell script
$ http://localhost:3002/subscribers/id
```

```javascript
router.patch('/:id', getSubscriber, async (req, res) => {
    if (req.body.name != null) {
        res.subscriber.name = req.body.name
    }
    if (req.body.subscribedToChannel != null) {
        res.subscriber.subscribedToChannel = req.body.subscribedToChannel
    }
    try {
        const updatedSubscriber = await res.subscriber.save();
        res.json(updatedSubscriber)
    } catch (err) {
        res.status(400).json({message: err.message})
    }
});
```

![#f93e3e](https://placehold.it/15/f93e3e/000000?text=+) **DELETE** _request to delete one subscriber by `/id`_

```shell script
$ http://localhost:3002/subscribers/id
```

```javascript
router.delete('/:id', getSubscriber, async (req, res) => {
    try {
        await res.subscriber.remove();
        res.json({message: 'Deleted Subscriber'})
    } catch (err) {
        res.status(500).json({message: err.message})
    }
});
```


## How to start the project
- Install [MongoDB](http://www.codebind.com/mongodb/install-mongodb-mac-os-x/)
- Run it locally `$ brew services start mongodb-community`
- Lunch server `$ yarn start`
