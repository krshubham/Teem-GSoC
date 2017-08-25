## Trello with Teem

### Challenges to solve:

- Add an option for integrating Teem with Trello

- Whenever someone makes a new need it should automatically be added to their correpsonding trello board at the same time

- When someone changes the status of a need in Teem it should automatically update the model in trello by either archiving / unarchiving.


### Implementation key points:

+ We add a new button in the Teem page giving the user an option to connect Trello with their Teem.

+ When they click on Integrate Trello, they are taken to Trello's OAuth api page where they sign in with their Trello credentials and then we get the token from Trello which is stored in the model of the project itself.

+ Every request that we make now picks up the data from this token only!

+ We have some methods added in [`trelloService.js`](https://github.com/krshubham/teem/blob/trello-in-project/src/js/services/trelloService.js) which act as an abstraction above Trello API, allowing us to communicate easily.

### Submission details:

+ Branch of the repository: [trello-in-project](https://github.com/krshubham/teem/tree/trello-in-project)


**Note**: This post has one part which is [Trello-to-Teem-Connection]()
