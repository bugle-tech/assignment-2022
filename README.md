# assignment-2022
The assignment test used for interviews on early 2022

# Idea
The idea is to create a very simple [LMS (Learning Management System)](https://en.wikipedia.org/wiki/Learning_management_system), which basically covers the implementation of REST API endpoints for managing courses and users.

## Specifications
Following we will provide some model specifications which can be just a **starting point** in order to model the REST API endpoints. The specifications might not be followed strictly, so we will evaluate creativity and problem-solving capabilities towards the main goal, which is a REST API for managing courses and trainees. 

Feel free to change/improve the modeling and naming _at your will_. Again, it's not *strict*, just a starting point.

## Some useful scenarios (tips)
1. A `User` can be created and may contain attributes such as `email`, `roles`, `name`, etc
2. The User can be authenticated (hint: devise)
3. A "special User" (a.k.a admin) can manage a list of Users
4. The admin can manage `Courses`
5. A Course may contain attributes such as `title`, `description`, `thumbnail` etc
6. The Course thumbnail can be saved at the local filesystem (server) or some Cloud provider, such as AWS S3. It's up to you.
7. A Course may have `Chapters`
8. A Chapter may contain a `Content`, which can be a `Video`, `Quiz` etc. It's ok if the Chapter has only one type of content, i.e `Video`
9. A `Video` can be uploaded to the local filesystem (server) or some Cloud provider, you're free to choose one or both
10. A Course may have an `Audience`, which will be the Users allowed to see the Course
11. A User may see and take Courses

Here's a sample diagram:

<img width="100%" alt="Screenshot 2022-01-21 at 13 48 15" src="https://user-images.githubusercontent.com/385640/150537856-c1a3498a-c881-4651-a097-b735eb56b60c.png">

## The REST API
The expectation is basically running a simple REST API alongside with some scenarios. Following some tips for starting point.

### Sign In / Sign Up

Hint: Devise
```
POST /signup
POST /signin
```

### Managing users
Admins are `Users`. But only Admins can manage Users. 
```
POST /users
GET  /users
GET  /users/{id}
```

### Managing courses
Only Admins can manage Courses.
```
POST /courses
GET  /courses
GET  /courses/{id}
```
Adding/Removing Chapters on Courses.
```
POST   /courses/{course_id}/chapters
GET    /courses/{course_id}/chapters
DELETE /courses/{course_id}/chapters/{id}
```
Adding/Removing "Content" (Video etc) to Chapters.
```
POST   /courses/{course_id}/chapters/{chapter_id}/content
```

### Manage audience
Adding/Removing Users (students) on Courses audience.
```
POST   /courses/{course_id}/audience
GET    /courses/{course_id}/audience
DELETE /courses/{course_id}/audience/{user_id}
```
### List Courses for a User (student)
Students can see a list of courses in which they are audience.
```
GET /my-courses
```
Students can take courses (watch `Videos`, for example)
```
GET /my-courses/{course_id}/take
```

# Considerations

* We don't expect a strict deadline, but we estimate that a week should be reasonable to implement the assignment
* We don't expect the assignment to follow all the requirements. We evaluate code quality, creativity, problem-solving capabilities
* We expect the application to be shared with us somehow, through platforms such as Github, Gitlab etc
* Bonus points: deploy, CI, integration with cloud services
* Bonut points plus plus: UI, a.k.a some frontend consuming the API
* Feel free to drop any questions at any time regarding the requuirements and during the assingment
