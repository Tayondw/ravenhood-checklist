# RavenHood Kanban Project Board Cards

The following cards will guide the implementation of the RobinHood API. Each
section should be copied into it's own card on the Kanban project board.
Each feature's progress should be tracked by checking off requirements as they
are met and progressing the cards from the `Backlog`, `Next Tasks`,
`In Progress`, `In Review`, and `Accepted` columns.

## Notes

The first two cards, "Authentication Required" and "Authorization Required" are
general tasks to be applied to endpoints that will need these requirements.  There will be a note dictating
whether the API Documentation for an endpoint needs any kind of
authentication or authorization

Sign Up, Log In, and Get Current User endpoints are a mandatory part of the API project,
and as such will be created and completed first. Ensuring that adding and testing the
functionality for Users' `firstName`,`lastName`, and `email` properties.

## Kanban Cards

Copy each of the following sections into its own card on a Kanban board for the
project. Github Kanban boards use markdown formatting, allowing these sections
to be copied directly:

### GitHub Setup

For this project, the README.md file will include the API documentation and the database schema for the API project that is being implemented.

- [X] Create a project folder and README for the project of group choice (TO BE COMPLETED BY WEEK 19 - DAY 1)
- [X] Create a Feature List that briefly describes the functionality of each feature that will be implemented (TO BE COMPLETED BY WEEK 19 - DAY 2)
- [X] Create a DB Schema that shows the tables and columns needed for features and their relationship (TO BE COMPLETED BY WEEK 19 - DAY 3)
- [X] Create a User Stories that details the relationship of the features from the Feature List from the a User point of view (TO BE COMPLETED BY WEEK 19 - DAY 4)
- [ ] Discuss wireframing of RavenHood based off of User Stories, Feature List, and the layout of RobinHood
- [ ] Create a Scrum Board detailing the flow of the project - discuss what the members of the group will be doing for the project, what can be contributed and how it will all come together (TO BE COMPLETED BY WEEK 19 - DAY 5)
- [ ] Create a `.gitignore` that ignores `*.db`, `.env`, `build`, `__pycache__` - see attached .gitignore for examples and what they pertain to
- [ ] Ensure there are more branches besides main. Branches to consider: `dev`, `auth-setup`, `login`, `sign-up`, `logout`, `get-session`, `validate-login-inputs`, `validate-signup-inputs`, `feature-1`, `feature-2`
- [ ] Impose branch protection rules for each branch
- [ ] Push to dev at the end of each day, discuss with teammates on what was completed and who completed what
- [ ] Push to main ONLY when ready to test to Render

### Authentication Required

All endpoints that require a current user to be logged in receive a standard authentication response.

- [ ] Authentication middleware responds with error status 401 when authentication is not provided

### Authorization Required

All endpoints that require a current user to have the correct role(s) or permission(s) receive a standard authorization response.

- [ ] Authorization middleware responds with error status 403 when an authenticated user does not have the correct role(s) or permission(s)

### Sign Up a User

Creates a new user, logs them in as the current user, and returns the current user's information.

- [ ] New user exists in the database after request
- [ ] Successful response includes newly created `id`, `first_name`, `last_name`, `email`, and `username`
- [ ] Error response with status 500 is given when the specified email or username already exists
- [ ] Error response with status 400 is given when body validations for the
  `email`, `first_name`, `username`, `last_name`, `location`, `phone`, `ssn`, or `birthday`, are violated

### Log In a User

Logs in a current user with valid credentials and returns the current user's information.

- [ ] Successful response includes the user's `id`, `first_name`, `last_name`, and `email`
- [ ] Error response with status 401 is given when invalid credentials are given
- [ ] Error response with status 400 is given when body validations for the
  `email`, `first_name`, or `last_name` are violated

### Get the Current User

Returns the information about the current user that is logged in.

- [ ] An authenticated user is required for a successful response
- [ ] Successful response includes the user's `id`, `first_name`, `last_name`, and `email`

### Get all Stocks

Returns all stocks.

- [ ] Seed data exists in the database for stocks to be returned.
- [ ] Successful response includes each stock in the database.
- [ ] Stock data returned includes the `id`, `company_name`, `ticker_symbol`, `description`,
  `current_price`, `ceo`, `employees`, `headquarters`, `createdAt`, `updatedAt`, `founded`, `market_cap`, `price_earnings_ratio`, `dividend_yield`, `average_volume`, `high_today`, `low_today`, `open_price`, `volume`, `fifty_two_week_high`, and `fifty_two_week_low`

### Get all Stocks added to a WatchList by the Current User

Returns all the stocks in a watchlist created by the current user.

- [ ] An authenticated user is required for a successful response
- [ ] Successful response includes only watchlists created current user
- [ ] WatchList data returned includes the `id`, `user_Id`, `name`, `createdAt`, and `updatedAt`

### Get details of a Stock from an id

Returns the details of a stock specified by its id.

- [ ] Successful response includes data only for the specified stock
- [ ] Stock data returned includes the `id`, `company_name`, `ticker_symbol`, `description`, `current_price`, `ceo`, `employees`,`headquarters`, `createdAt`, `updatedAt`, `founded`, `market_cap`, `price_earnings_ratio`, `dividend_yield`, `average_volume`, `high_today`, `low_today`, `open_price`, `volume`, `fifty_two_week_high`, and `fifty_two_week_low`
- [ ] Stock data returns associated data for `Watch_List_Stocks`, a list of dicts of stock data in the watch_list including the `id`, `stock_id`, and `watch_list_id`
- [ ] Watch_List data returns associated data for `Current User`, including the `id`, `first_name`, and `last_name`
- [ ] Error response with status 404 is given when a stock does not exist with the provided `id`

### Create a Portfolio

Creates and returns a new portfolio.

- [ ] An authenticated user is required for a successful response
- [ ] New portfolio exists in the database after request
- [ ] Portfolio data returned includes the `id`, `user_Id`, `portfolio_name`, `cash_balance`, `total_amount`, `is_active`, `createdAt`, and `updatedAt`
- [ ] Error response with status 400 is given when body validations for the `portfolio_name`, `cash_balance`, `total_amount`, or `is_active`, are violated

### Add a Portfolio to a User based on the User's id

Create and return a new portfolio for a user specified by id.

- [ ] An authenticated user is required for a successful response
- [ ] Only the current user is authorized to add a portfolio
- [ ] New portfolio exists in the database after request
- [ ] Portfolio data returned includes the `id`, `portfolio_name`, `cash_balance`, and `total_amount`
- [ ] Error response with status 404 is given when a user does not exist with the provided `id`

### Get all Portfolios by the Current User

Returns all the portfolios created by the current user.

- [ ] An authenticated user is required for a successful response
- [ ] Successful response includes only portfolios created current user
- [ ] Portfolio data returned includes the `id`, `user_Id`, `portfolio_name`, `cash_balance`, `total_amount`, `is_active`, `createdAt`, and `updatedAt`

### Edit a Portfolio

Updates and returns an existing portfolio.

- [ ] An authenticated user is required for a successful response
- [ ] Only the current user is authorized to edit
- [ ] Portfolio record is updated in the database after request
- [ ] Portfolio data returned includes the `id`, `user_id`, `portfolio_name`, `cash_balance`, `total_amount`, `is_active`, `createdAt`, and `updatedAt`
- [ ] Error response with status 400 is given when body validations for the `portfolio_name`, `cash_balance`, `total_amount`, or `is_active`, are violated
- [ ] Error response with status 404 is given when a portfolio does not exist with the provided `id`

### Delete a Portfolio

Deletes an existing portfolio.

- [ ] An authenticated user is required for a successful response
- [ ] Only the current user is authorized to delete
- [ ] Portfolio record is removed from the database after request
- [ ] Success response includes a `message` indicating a successful deletion
- [ ] Error response with status 404 is given when a portfolio does not exist with the provided `id`

### Get all Transactions for a Portfolio specified by id

Returns all transactions for a portfolio specified by its id.

- [ ] Seed data exists in the database for transactions to be returned.
- [ ] Successful response includes each transaction for a portfolio in the database.
- [ ] Transaction data returned includes `id`, `portfolio_id`, `type`, `date`, `stock`, `quantity`, and `transaction_price`

### Create a new Transaction for a Portfolio specified by its id

Creates and returns a new transaction for a portfolio specified by its id

- [ ] An authenticated user is required for a successful response
- [ ] Only the current user is authorized to create a transaction
- [ ] New transaction exists in the database after request
- [ ] Transaction data returned includes `id`, `portfolio_id`, `type`, `date`, `stock`, `quantity`, and `transaction_price`
- [ ] Error response with status 404 is given when a portfolio does not exist with the provided `id`
- [ ] Error response with status 400 is given when body validations for the `type`, `date`, `stock`, `quantity`, or `transaction_price` are violated

### Delete a Transaction

Cancels an existing transaction.

- [ ] An authenticated user is required for a successful response
- [ ] Only the current user is authorized to delete
- [ ] Transaction record is removed from the database after request
- [ ] Success response includes a `message` indicating a successful deletion
- [ ] Error response with status 404 is given when a transaction does not exist with the provided `id`

### Create a Watch_List for a User specified by its id

Creates and returns a new watch_list for a user specified by its id

- [ ] An authenticated user is required for a successful response
- [ ] Only the current user is authorized to create an watch_list
- [ ] New watch_list exists in the database after request
- [ ] Watch_List data returned includes `id`, `user_id`, `stock_id`, and `name`
- [ ] Error response with status 400 is given when body validations for the `user_id`, `name`, or `stock_id` are violated
- [ ] Error response with status 404 is given when a stock does not exist with the provided `id`

### Get all Watch_Lists of a User specified by its id

Returns all the watch_lists of a user specified by its id

- [ ] Seed data exists in the database for watch_lists to be returned.
- [ ] Successful response includes only watch_lists for the specified user
- [ ] Watch_List data returned includes the `id`, `user_id`, `stock_id`,  and `name`
- [ ] Watch_List data returned includes aggregate data for `totalLists`
- [ ] Watch_List data returned includes associated `Stock` data, including `id`, `name`, `ticker_symbol`, and `current_price`
- [ ] Watch_List data returned includes associated `User` data, including `id`, `first_name`, and `last_name`
- [ ] Error response with status 404 is given when a stock, user, or watch_list does not exist with the provided `id`

### Get details of a Watch_List specified by its id

Returns the details of a watch_list specified by its id.

- [ ] Successful response includes data only for the specified watch_list
- [ ] Watch_List data returned includes the `id`, `user_id`, `stock_id`, and `name`
- [ ] Watch_List data returned includes aggregate data for `totalStocks`
- [ ] Watch_List data returned includes associated `Stock` data, including `id`, `name`, `ticker_symbol`, and `current_price`
- [ ] Watch_List data returned includes associated `User` data, including `id`, `first_name`, and `last_name`
- [ ] Error response with status 404 is given when a stock, user, or watch_list does not exist with the provided `id`

### Add a Stock to a Watch_List based on the Watch_List's id

Create and return a new stock for a watch_list specified by id.

- [ ] An authenticated user is required for a successful response
- [ ] Only the current user is authorized to add a stock
- [ ] New stock exists in the database after request
- [ ] Watch_List data returned includes the `id`, `stock_id`, `name`, `ticker_symbol`, and `current_price`
- [ ] Error response with status 404 is given when an watch_list or stock does not exist with the provided `id`

### Edit a Watch_List specified by its id

Edit and returns a watch_list specified by its id

- [ ] An authenticated user is required for a successful response
- [ ] Only the current user is authorized to edit a watch_list
- [ ] Watch_List record is updated in the database after request
- [ ] Watch_List data returned includes the `id`, `user_id`, `stock_id`, and `name`
- [ ] Error response with status 400 is given when body validations for the `user_id`, `name`, or `stock_id` are violated
- [ ] Error response with status 404 is given when a watch_list or stock does not exist with the provided `id`

### Delete a Watch_List specified by its id

Delete a watch_list specified by its id

- [ ] An authenticated user is required for a successful response
- [ ] Only the current user is authorized to delete a watch_list
- [ ] Watch_List record is removed from the database after request
- [ ] Success response includes a `message` indicating a successful deletion
- [ ] Error response with status 404 is given when a watch_list does not exist with the provided `id`

### Add Query Filters to Get All Stocks

Return stocks filtered by query parameters.

- [ ] Query parameters are accepted for `page`, `size`, `company_name`, and `ticker_symbol`
- [ ] Default values are provided for the `page` and `size` parameters
- [ ] Successful response includes only stocks in the database that meet the specified query parameters criteria
- [ ] Stock data returned includes the `id`, `company_name`, `ticker_symbol`, `description`,
  `current_price`, `ceo`, `employees`, `headquarters`, `createdAt`, `updatedAt`, `founded`, `market_cap`, `price_earnings_ratio`, `dividend_yield`, `average_volume`, `high_today`, `low_today`, `open_price`, `volume`, `fifty_two_week_high`, and `fifty_two_week_low`
- [ ] Stock data returned includes aggregate data for `num_stocks`
- [ ] Stock data returns associated data for `Watch_List_Stocks`, a list of dicts of stock data in the watch_list including the `id`, `stock_id`, and `watch_list_id`
- [ ] Stock data returns associated data for `Current User`, including the `id`, `first_name`, and `last_name`
- [ ] Successful response includes the `page` and `size` of the returned payload
- [ ] Error response with status 400 is given when query parameter validations for the `page`, `size`, `company_name`, or `ticker_symbol` are violated
