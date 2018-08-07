# Y2 2018 Summer: Forms Lab

Welcome to the forms lab! (Note that this comes after the
[routing lab](meet-projects/y2s18-routing).) Please read all the
instructions so you don't get lost halfway through, but definitely
feel free to ask for help if you get stuck. Good luck, and have fun!

## Setup

Before you start coding, make sure you clone the repository for this lab:
```
cd ~/Desktop
git clone https://github.com/meet-projects/y2s18-forms.git
subl y2s18-forms
```

## Lecture Exercises

**Important**: Work in the `exercises` folder!

### Part 1: Routing Review

In `app.py`, add a route to `/add` to return the `add.html` template.

### Part 2: HTTP Methods

Edit your method for the route to `/add` so that it takes both GET and
POST requests.

If a GET request comes in, return the `add.html` template like before,
but if a POST request comes in, print `'Received POST request!'`
(remember `print` statements?) and then return the same template.

### Part 3: Creating a Form

In the `add.html` template, between the `<form>` tags, add two `<input>`
tags, one with `name=student_name` and one with `name=student_year`.
Add one more `<input>` tag, this time with `type=submit` and `value=Submit`.

### Part 4: POSTing Forms

Now we need to add to the POST method of the `/add` route we have created
in `app.py`. If the request is a POST request, add the information from
the article to the database.

*Hint*: The `name` of the form element corresponds to the value of that
element in `request.form`.

## Independent Lab: Deleting an entry

**Important**: Work in the `lab` folder!

### Part 1

In `student.html`, add a `<form>` tag somewhere that has one `<input>`
element with `type="submit"` and `value="delete"`. Edit the form element
so that when submitted, it makes a POST to `/delete/<student_id>`, where
the `student_id` is of the article currently being viewed. *Hint*: You
will need to change the `action` and `method` attributes of `<form>`.

### Part 2

In `app.py`, create a new route to `/delete/<int:student_id>` that
only accepts POST requests.

### Part 3

In the new route, use the database functions you've already created to
delete the student entry with the given `student_id`.

### Part 4

Then redirect the user back to the home page by returning the home page
using one of the Flask functions we've learned.
*Hint*: Use `redirect(url_for())`.

### Part 5

You can now make your website look prettier using CSS and additional
templating, as you've learned in the past few days.

## Lab Bonus: Updating an entry

### Part 1

For this part, you'll need to create a new template called `edit.html`.
Make sure you place it in the `templates` folder!

### Part 2

Add a form to this new template for editing a student's `finished_lab`
status. What information is necessary to edit the database entry?

### Part 3

In `app.py`, add a new route to `/edit/<int:student_id>`. When a GET
request is made to this route, it should return the template we just made.
When a POST request is made to this route, it should make a database call
to update the given entry and then return the student's page.

### Part 4

In `student.html`, add a link to the new route for editing. You should
now be able to navigate the website and add new students, delete students,
and update whether individual students have completed their labs.

## Additional bonuses

1. Add a way to search for student by name, using GET query string parameters.

2. Figure out a way to add a photo to each student's page.

3. Incorporate some CSS animations.