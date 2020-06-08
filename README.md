# Challenge: fundamental concepts with Node.JS

This challenge is part of the [RocketSeat](https://rocketseat.com.br/) GoStack Bootcamp.

This is a small application using Node.JS and TypeScript that follows patterns using the concept of models, repositories and services.

This application stores inbound and outbound financial transactions, allowing the user to create new transactions and list them all.

## Routes

- **`POST /transactions`**: This route receives `title`, `value` and `type` in the request body, where `type` is the type of transaction (income or outcome). When creating a new transaction, it must be stored in the object following the format below:

```json
{
  "id": "uuid",
  "title": "Salary",
  "value": 3000,
  "type": "income"
}
```

- **`GET /transactions`**: This route must return a list with all transactions stored up until the moment, including the total value of income, outcome and a balance. The object returned must follow the format below:

```json
{
  "transactions": [
    {
      "id": "uuid",
      "title": "Salary",
      "value": 4000,
      "type": "income"
    },
    {
      "id": "uuid",
      "title": "Freelancer",
      "value": 2000,
      "type": "income"
    },
    {
      "id": "uuid",
      "title": "Invoice payment",
      "value": 4000,
      "type": "outcome"
    }
  ],
  "balance": {
    "income": 6000,
    "outcome": 4000,
    "total": 2000
  }
}
```

## Tests

- **`should be able to create a new transaction`**: In order to pass this test, the application must allow the creation of a new transaction, returning the json object of the new transaction.

- **`should be able to list the transactions`**: In order to pass this test, the application must return a json object containing a list of all transactions stored and the balance details.

- **`should not be able to create outcome transaction without a valid balance`**: In order to pass this test, the application must not allow that a new transaction with the type `outcome` extrapolate the available balance. The application must return a response with HTTP code 400 and an error message like `{ error: string }` .
