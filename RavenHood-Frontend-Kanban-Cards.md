# RavenHood Frontend Kanban Card Checklist

## Authetication Requirements

### Feature: Application Header

- [ ] On every page of the site, the browser tab shows the app name and fav icon
- [ ] On every page of the site, the logo is on the top left of the page
- [ ] On every page of the site, clicking the logo returns the user to the home page (`/`)
- [ ] As the browser is resized, the header's width adjusts dynamically so the logo stays on the left, and the auth/user buttons stay on the right.
- [ ] The layout and element positioning is equivalent to the wireframes.

### Feature: Log in

- [ ] On every page of the site, a `"Log in"` button (or drop down menu containing `"Log in"`) must be at the top-right of the page.
- [ ] If using a drop down menu, the menu must contain a `"Log in"` menu option.
- [ ] If using a drop down menu, the menu must contain a `"Sign up"` menu option.
- [ ] Upon clicking the `"Log in"` button or menu option, it opens a modal pop-up that prompts the Username and Password input boxes and a `"Log in"` button.
- [ ] Within the modal, the `"Log in"` button must be disabled anytime the username is less than 4 characters or the password is less than 6 characters.
- [ ] Attempting to log in with an invalid username or password must prompt the error message "The provided credentials were invalid".
- [ ] Upon logging in with a valid username and password, it must successfully log-in the user and sets their session cookie.
- [ ] Upon logging in with a valid username and password, the `"Log in"` and `"Sign up"` buttons at the top of the page are hidden.
- [ ] Upon logging in with a valid username and password, it shows the User Menu Button (see next feature).
- [ ] In the log-in modal, an extra link or button is available with the label "Log in as Demo User". Upon clicking this "Log in as Demo User" button, it will log the user into the "demo" account.
- [ ] Upon closing the log-in modal, it resets errors and clears all data entered. When it reopens it will be in the default state (empty inputs and disabled button).
- [ ] The layout and element positioning is equivalent to the wireframes.

### Feature: User Menu and Log Out

- [ ] On every page of the site, I should be able to see a User Menu Button in the upper-right corner that opens a user drop down menu when clicked.
- [ ] After a user successfully logs in, The user drop down menu contains the logged in user's first name as a greeting: `"Hello, "<first name>"`.
- [ ] After a user successfully logs in, The user drop down menu contains the logged in user's email: `<email>`.
- [ ] After a user successfully logs in, The user drop down menu contains: a `Log out` Button as a menu option.
- [ ] After a user successfully logs in, the user menu does NOT contain the ``"Log in"`` or ``"Sign up"`` menu options.
- [ ] Upon clicking anywhere outside the User Menu (including on the User Menu Button), the menu drop down hides.
- [ ] Upon clicking anywhere on the greeting or email inside the user drop down menu, the User Menu remains open.
- [ ] Upon clicking the `"Log out"` menu option, it performs a log out where it will clear the session/cookie.
- [ ] Upon clicking the `"Log out"` button, it performs a log out where it will close the user drop down menu.
- [ ] Upon clicking the `"Log Out"` button, it performs a log out where it will navigate the user to the home page (`/`).
- [ ] The layout and element positioning is equivalent to the wireframes.

### Feature: Sign Up

- [ ] When logged out, I should see a ``"Sign up"`` button next to the ``"Log in"`` button (or drop down menu containing a ``"Sign up"`` menu option below a `"Log in"` menu option) in the top-right corner of the header on every page of the site.
- [ ] Upon clicking ``"Sign up"`` to open the sign-up modal pop-up window, a new user account form.
- [ ] The new user account form should show placeholders or labels and input boxes for: `"First Name"`, `"Last Name"`, `"Email"`, `"Username"`, `"Password"`, and `"Confirm Password"`.
- [ ] The new user account form should show a `"Sign up"` button after all the input boxes.
- [ ] The `"Sign up"` button should be disabled when any field is empty.
- [ ] The `"Sign up"` button should be disabled when the `"Username"` field is less than 4 characters.
- [ ] The `"Sign up"` button should be disabled when the `"Password"` field is less than 6 characters.
- [ ] When clicking `"Sign up"` button on the new user account form with errors in the form, it must show all error messages returned from the backend (similar to the following): "The provided email is invalid" or "Username must be unique".
- [ ] Upon closing and reopening sign-up modal, the errors are reset (all errors displayed before closing the modal are gone).
- [ ] Upon closing and reopening sign-up modal, all fields are empty (all data entered before has been cleared).
- [ ] Upon closing and reopening sign-up modal, the `"Sign up"` button on the new user account form is disabled.
- [ ] After a successful sign-up is completed, the new user should automatically be logged in and see the User Menu with their information entered during sign-up with a `"Log out"` menu option, but not `"Log in"` or `"Sign up"` menu options.
- [ ] After a successful sign-up is completed, if the new user refreshes the browser, they should still see the User Menu Button with the new user's information in the user drop down menu.
- [ ] The layout and element positioning is equivalent to the wireframes.

## Application Requirements

### Feature: Landing Page - Not Logged In

- [ ] The landing page (`/`) contains four sections vertically aligned.
- [ ] Section 1 has a title and intro text in the center.
- [ ] Section 2 has info cards or heading and subtext on the left and infographic on the right.
- [ ] Section 3 has three columns each with an icon, link with an underline and pointer cursor when the mouse rolls over it, and a caption.
- [ ] Section 3's first column has a link with the text "See all groups"
- [ ] Section 3's second column has a link with the text "Find an event"
- [ ] Section 3's third column has a link with the text "Start a group" (if the user is not logged in, then this link is disabled - light grey text with no rollover or click events)
- [ ] Section 4 has a "Join Meetup" button centered horizontally.
- [ ] The layout and element positioning is equivalent to the wireframes.

### Feature: Landing Page - Logged In
