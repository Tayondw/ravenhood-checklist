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
- [ ] Ensure there are more branches besides main. Branches to consider: `dev`, `auth-setup`, `login`, `sign-up`, `logout`, `get-session`, `validate-login-inputs`, `validate-signup-inputs`
- [ ] Impose branch protection rules for each branch

### Authentication Required

All endpoints that require a current user to be logged in receive a standard
authentication response.

- [X] Authentication middleware responds with error status 401 when
  authentication is not provided


### Authorization Required

All endpoints that require a current user to have the correct role(s) or
permission(s) receive a standard authorization response.

- [X] Authorization middleware responds with error status 403 when
  an authenticated user does not have the correct role(s) or permission(s)


### Sign Up a User

Creates a new user, logs them in as the current user, and returns the current
user's information.

- [X] New user exists in the database after request
- [X] Successful response includes newly created `id`, `firstName`, `lastName`,
  and `email`
- [X] Error response with status 500 is given when the specified email or username
  already exists
- [X] Error response with status 400 is given when body validations for the
  `email`, `firstName`, or `lastName` are violated


### Log In a User

Logs in a current user with valid credentials and returns the current user's
information.

- [X] Successful response includes the user's `id`, `firstName`, `lastName`,
  and `email`
- [X] Error response with status 401 is given when invalid credentials are given
- [X] Error response with status 400 is given when body validations for the
  `email`, `firstName`, or `lastName` are violated


### Get the Current User

Returns the information about the current user that is logged in.

- [X] An authenticated user is required for a successful response
- [X] Successful response includes the user's `id`, `firstName`, `lastName`,
  and `email`


### Get all Groups

Returns all groups.

- [X] Seed data exists in the database for groups to be returned.
- [X] Successful response includes each group in the database.
- [X] Group data returned includes the `id`, `organizerId`, `name`, `about`,
  `type`, `private`, `city`, `state`, `createdAt`, `updatedAt`, `numMembers`,
  and `previewImage`


### Get all Groups joined or organized by the Current User

Returns all the groups either created by the current user or those where the
current user has a membership.

- [X] An authenticated user is required for a successful response
- [X] Successful response includes only groups created or joined by the current
  user
- [X] Group data returned includes the `id`, `organizerId`, `name`, `about`,
  `type`, `private`, `city`, `state`, `createdAt`, `updatedAt`, `numMembers`,
  and `previewImage`


### Get details of a Group from an id

Returns the details of a group specified by its id.

- [X] Successful response includes data only for the specified group
- [X] Group data returned includes the `id`, `organizerId`, `name`, `about`,
  `type`, `private`, `city`, `state`, `createdAt`, `updatedAt`, and `numMembers`
- [X] Group data returns associated data for `GroupImages`, an array of image
  data including the `id`, `url`, and `preview`
- [X] Group data returns associated data for `Organizer`, including the `id`,
  `firstName`, and `lastName`
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`


### Create a Group

Creates and returns a new group.

- [X] An authenticated user is required for a successful response
- [X] New group exists in the database after request
- [X] Group data returned includes the `id`, `organizerId`, `name`, `about`,
  `type`, `private`, `city`, `state`, `createdAt`, and `updatedAt`
- [X] Error response with status 400 is given when body validations for the
  `name`, `about`, `type`, `private`, `city`, or `state` are violated


### Add an Image to a Group based on the Group's id

Create and return a new image for a group specified by id.

- [X] An authenticated user is required for a successful response
- [X] Only the organizer of the group is authorized to add an image
- [X] New image exists in the database after request
- [X] Image data returned includes the `id`, `url`, and `preview`
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`


### Edit a Group

Updates and returns an existing group.

- [X] An authenticated user is required for a successful response
- [X] Only the owner of the group is authorized to edit
- [X] Group record is updated in the database after request
- [X] Group data returned includes the `id`, `organizerId`, `name`, `about`,
  `type`, `private`, `city`, `state`, `createdAt`, and `updatedAt`
- [X] Error response with status 400 is given when body validations for the
  `name`, `about`, `type`, `private`, `city`, or `state` are violated
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`


### Delete a Group

Deletes an existing group.

- [X] An authenticated user is required for a successful response
- [X] Only the owner of the group is authorized to delete
- [X] Group record is removed from the database after request
- [X] Success response includes a `message` indicating a successful deletion
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`


### Get all Venues for a Group specified by id

Returns all venues for a group specified by its id.

- [X] Seed data exists in the database for venues to be returned.
- [X] Successful response includes each venue for a group in the database.
- [X] Venue data returned includes `id`, `groupId`, `address`, `city`, `state`,
  `lat`, and `lng`


### Create a new Venue for a Group specified by its id

Creates and returns a new venue for a group specified by its id

- [X] An authenticated user is required for a successful response
- [X] Only the owner of the group or a member of the group with a membership
  status of "co-host" is authorized to create a venue
- [X] New venue exists in the database after request
- [X] Venue data returned includes `id`, `groupId`, `address`, `city`, `state`,
  `lat`, and `lng`
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`
- [X] Error response with status 400 is given when body validations for the
  `address`, `city`, `state`, `lat`, or `lng` are violated


### Edit a Venue specified by its id

Edit a new venue specified by its id

- [X] An authenticated user is required for a successful response
- [X] Only the owner of the group or a member of the group with a membership
  status of "co-host" is authorized to edit a venue
- [X] Venue record is updated in the database after request
- [X] Venue data returned includes `id`, `groupId`, `address`, `city`, `state`,
  `lat`, and `lng`
- [X] Error response with status 404 is given when a venue does not exist with
  the provided `id`
- [X] Error response with status 400 is given when body validations for the
  `address`, `city`, `state`, `lat`, or `lng` are violated

### Get all Events

Returns all the events.

- [X] Seed data exists in the database for events to be returned.
- [X] Successful response includes each event in the database.
- [X] Event data returned includes the `id`, `groupId`, `venueId`, `name`,
  `type`, `startDate`, `endDate`, and `previewImage`
- [X] Event data returned includes aggregate data for `numAttending`
- [X] Event data returned includes associated `Group` data, including `id`,
  `name`, `city`, and `state`
- [X] Event data returned includes associated `Venue` data, if any, including
  `id`, `city`, and `state`


### Get all Events of a Group specified by its id

Returns all the events of a group specified by its id

- [X] Seed data exists in the database for events to be returned.
- [X] Successful response includes only events for the specified group
- [X] Event data returned includes the `id`, `groupId`, `venueId`, `name`,
  `type`, `startDate`, `endDate`, and `previewImage`
- [X] Event data returned includes aggregate data for `numAttending`
- [X] Event data returned includes associated `Group` data, including `id`,
  `name`, `city`, and `state`
- [X] Event data returned includes associated `Venue` data, if any, including
  `id`, `city`, and `state`
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`


### Get details of an Event specified by its id

Returns the details of an event specified by its id.

- [X] Successful response includes data only for the specified event
- [X] Event data returned includes the `id`, `groupId`, `venueId`, `name`,
  `description`, `type`, `capacity`, `price`, `startDate`, and `endDate`
- [X] Event data returned includes aggregate data for `numAttending`
- [X] Event data returned includes associated `Group` data, including `id`,
  `name`, `private`, `city`, and `state`
- [X] Event data returned includes associated `Venue` data, if any, including
  `id`, `address`, `city`, `state`, `lat`, and `lng`
- [X] Event data returns associated data for `EventImages`, an array of image
  data including the `id`, `url`, and `preview`
- [X] Error response with status 404 is given when an event does not exist with
  the provided `id`


### Create an Event for a Group specified by its id

Creates and returns a new event for a group specified by its id

- [X] An authenticated user is required for a successful response
- [X] Only the owner of the group or a member of the group with a membership
  status of "co-host" is authorized to create an event
- [X] New event exists in the database after request
- [X] `venueId` can be `null`
- [X] Event data returned includes `id`, `groupId`, `venueId`, `name`, `type`,
  `capacity`, `price`, `description`, `startDate` and `endDate`
- [X] Error response with status 400 is given when body validations for the
  `venueId`, `name`, `type`, `capacity`, `price`, `description`, `startDate`,
  or `endDate` are violated
- [X] Error response with status 404 is given when a venue does not exist with
  the provided `id`


### Add an Image to an Event based on the Event's id

Create and return a new image for an event specified by id.

- [X] An authenticated user is required for a successful response
- [X] Only an attendee of the event is authorized to add an image
- [X] New image exists in the database after request
- [X] Image data returned includes the `id`, `url`, and `preview`
- [X] Error response with status 404 is given when an event does not exist with
  the provided `id`


### Edit an Event specified by its id

Edit and returns an event specified by its id

- [X] An authenticated user is required for a successful response
- [X] Only the owner of the group or a member of the group with a membership
  status of "co-host" is authorized to create an event
- [X] Event record is updated in the database after request
- [X] Event data returned includes `id`, `groupId`, `venueId`, `name`, `type`,
  `capacity`, `price`, `description`, `startDate` and `endDate`
- [X] Error response with status 400 is given when body validations for the
  `venueId`, `name`, `type`, `capacity`, `price`, `description`, `startDate`,
  or `endDate` are violated
- [X] Error response with status 404 is given when a venue does not exist with
  the provided `id`
- [X] Error response with status 404 is given when an event does not exist with
  the provided `id`


### Delete an Event specified by its id

Delete an event specified by its id

- [X] An authenticated user is required for a successful response
- [X] Only the owner of the group or a member of the group with a membership
  status of "co-host" is authorized to create an event
- [X] Event record is removed from the database after request
- [X] Success response includes a `message` indicating a successful deletion
- [X] Error response with status 404 is given when an event does not exist with
  the provided `id`


### Get all Members of a Group based on the Group's id

Returns all the members of a group specified by its id.

- [X] Seed data exists in the database for members to be returned.
- [X] Successful response includes only members for the specified group
- [X] Member data returned includes the `id`, `firstName`, and `lastName` for
  each member
- [X] Member data returned includes the associated membership `status`
- [X] If you ARE the organizer of the group, members with a membership status of
  "pending" ARE included in the returned results
- [X] If you are NOT the organizer of the group, members with a membership
  status of "pending" are NOT included in the returned results
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`


### Request a Membership for a Group based on the Group's id

Request a new membership for a group specified by id.

- [X] An authenticated user is required for a successful response
- [X] New membership exists in the database after request
- [X] Success response includes the `groupId`, `memberId`, and a `status` of
  "pending"
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`
- [X] Error response with status 400 is given when the current user already has
  a pending membership for the group
- [X] Error response with status 400 is given when the current user already has
  an accepted membership for the group


### Change the status of a membership for a group specified by id

Change the status of a membership for a group specified by id.

- [X] An authenticated user is required for a successful response
- [X] Only the owner of the group or a member of the group with a membership
  status of "co-host" is authorized to change the status of a membership
- [X] Membership record is updated in the database after request
- [X] Success response includes the `id` `groupId`, `memberId`, and the new
  `status`
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`
- [X] Error response with status 403 is given when changing the status to
  "co-host" when the current user is not the group organizer
- [X] Error response with status 403 is given when changing the status to
  "member" when the current user is not the group organizer
  or a co-host
- [X] Error response with status 400 is given when changing the status to
  "pending"
- [X] Error response with status 404 is given when a membership between the user
  and group does not exist


### Delete membership to a group specified by id

Delete a membership to a group specified by id.

- [X] An authenticated user is required for a successful response
- [X] Only the owner/host of the group or the member themselves is authorized to
  delete the membership of a user to a group
- [X] Membership record is removed from the database after request
- [X] Success response includes a `message` indicating a successful deletion
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`
- [X] Error response with status 404 is given when a member does not exist with
  the provided `id`
- [X] Error response with status 403 is given when a request is made to delete
  another user's membership when the current user is not the group organizer


### Get all Attendees of an Event specified by its id

Returns the attendees of an event specified by its id.

- [X] Seed data exists in the database for attendees to be returned.
- [X] Successful response includes only attendees for the specified event
- [X] Attendee data returned includes the `id`, `firstName`, and `lastName` for
  each member
- [X] Member data returned includes the associated membership `status`
- [X] If you ARE the organizer of the group or a "co-host", attendees with an
  attendance status of "pending" ARE included in the returned results
- [X] If you are NOT the organizer of the group or a "co-host", attendees with
  an attendance status of "pending" are NOT included in the returned results
- [X] Error response with status 404 is given when an event does not exist with
  the provided `id`


### Request to Attend an Event based on the Event's id

Request attendance for an event specified by id.

- [X] An authenticated user is required for a successful response
- [X] New attendance exists in the database after request
- [X] Success response includes the `eventId`, `userId`, and a `status` of
  "pending"
- [X] Error response with status 404 is given when an event does not exist with
  the provided `id`
- [X] Error response with status 400 is given when the current user already has
  a pending attendance for the event
- [X] Error response with status 400 is given when the current user already is
  already an accepted attendee for the event


### Change the status of an attendance for an event specified by id

Change the status of an attendance for an event specified by id.

- [X] An authenticated user is required for a successful response
- [X] Only the owner of the group or a member of the group with a membership
  status of "co-host" is authorized to change the status of a membership
- [X] Attendance record is updated in the database after request
- [X] Success response includes the `id` `eventId`, `userId`, and the new
  `status`
- [X] Error response with status 404 is given when an event does not exist with
  the provided `id`
- [X] Error response with status 400 is given when changing the status to
  "pending"
- [X] Error response with status 403 is given when changing the status to
  "attending" when the current user is not the organizer or a co-host
- [X] Error response with status 404 is given when an attendance between the
  user and event does not exist


### Delete attendance to an event specified by id

Delete an attendance to an event specified by id.

- [X] An authenticated user is required for a successful response
- [X] Only the owner/host of the group or the member themselves is authorized to
  delete the attendance of a user to an event
- [X] Attendance record is removed from the database after request
- [X] Success response includes a `message` indicating a successful deletion
- [X] Error response with status 404 is given when a group does not exist with
  the provided `id`
- [X] Error response with status 404 is given when a member does not exist with
  the provided `id`
- [X] Error response with status 403 is given when a request is made to delete
  another user's membership when the current user is not the group organizer


### Delete an Image for a Group

Delete an existing image for a Group.

- [X] An authenticated user is required for a successful response
- [X] Only the organizer or co-host of the group is authorized to delete
- [X] Image record is removed from the database after request
- [X] Success response includes a `message` indicating a successful deletion
- [X] Error response with status 404 is given when a group image does not exist
  with the provided `id`


### Delete an Image for an Event

Delete an existing image for an Event.

- [X] An authenticated user is required for a successful response
- [X] Only the organizer or co-host of the group is authorized to delete
- [X] Image record is removed from the database after request
- [X] Success response includes a `message` indicating a successful deletion
- [X] Error response with status 404 is given when an image does not exist with
  the provided `id`


### Add Query Filters to Get All Events

Return events filtered by query parameters.

- [X] Query parameters are accepted for `page`, `size`, `name`, `type` and
  `startDate`
- [X] Default values are provided for the `page` and `size` parameters
- [X] Successful response includes only events in the database that meet the
  specified query parameters criteria
- [X] Event data returned includes the `id`, `groupId`, `venueId`, `name`,
  `type`, `startDate`, `endDate`, and `previewImage`
- [X] Event data returned includes aggregate data for `numAttending`
- [X] Event data returned includes associated `Group` data, including `id`,
  `name`, `city`, and `state`
- [X] Event data returned includes associated `Venue` data, if any, including
  `id`, `city`, and `state`
- [X] Successful response includes the `page` and `size` of the returned payload
- [X] Error response with status 400 is given when query parameter validations
  for the `page`, `size`, `name`, `type` or `startDate` are violated
