## Trello with Teem

The case is important when someone updates some data in Trello. We want to sync all this data at the same time to all the clients, but it has a lot of challenges!

### Challenges to solve:

+ Register webhook for every Teem integrated with Trello. Multiple webhooks may be registered if a single user links multiple Teems with Trello across a single user token.

+ When some changes happen in the Trello model, Trello sends a post request to the callback URL of the server provided while creating the webhook. More info about this [here](https://developers.trello.com/reference#webhooks)
	
	+  Since this happens for every change we get a post request for changes that we do on Teem also, and since the Webhook server and the Trello server are independent, things need to be coordinated properly between both of these servers in order to synchronize properly!
	
	+  Teem establishes a websocket connection with the SwellRT server which allows it to modify data simultaneously through the SwellRT api. Refer [here](https://github.com/P2Pvalue/swellrt/wiki/API-Reference-Web) for more info.
	
	+  When we tried to do the same using phantomJs we were not able to connect in the same way as Teem does, PhantomJs was weird in terms that it did not wait properly for events to occur!


**Caveats** : SwellRT doesn't have any way to run in non browser environments.

### Way to solve this problem:

The best way to solve this problem is by making some changes in the SwellRT API so that it either allows execution in non browser environments like node or by providing some kind of REST API that can be consumed by such webhook servers.

Once a request is issued by a webhook server, it should propagate this model change accross all clients currently active and part of the Teem.

### Submission details:

Whatever approaches I tried I have it in a repository. Its a good starting point to know why these approaches fail and then ponder over the main part of establishing connection between webhook server and the SwellRT server.

Repository: [krshubham/teem-trello-webhook-server](https://github.com/krshubham/teem-trello-webhook-server)

