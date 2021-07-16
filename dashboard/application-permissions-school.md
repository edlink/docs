Applications on the Edlink platform are created with specific permissions selected. These permissions grant an application the ability to read or change data in an integrated data source. Edlink is designed to give school administrators the ability to specifically see what data an application can access, before the integration is enabled.

The list of an application's requested permissions can be seen when viewing the ***Marketplace*** profile of the application.

![permissions](https://edlink.github.io/docs/media/dashboard/dev/application-permissions-school.jpg)

Below are the list of permissions you may see an application request:

### User Sign In Options
- **LTI Launch**: Allows end users to LTI launch into this application.
- **Single Sign On**: Allows end users to sign in using their credentials from the selected source.

### Application Permissions for the Source System
- **Create Schools**: The application can create schools in the source system.
- **Read Schools**: The application can read a list of the schools that are imported from a source.
- **Update Schools**: The application can update the schools that are imported from a source.
- **Delete Schools**: The application can delete schools within the source system.
- **Read Users**: The application can read a list of students, teachers, and school administrators.
- **Create Users**: This application can create users within the source system.
- **Update Users**: This application can update user data within the source system.
- **Delete Users**: The application can delete schools within the source system.
- **Create Courses**: This application can create courses within the source system.
- **Update Courses**: This application can update courses within the source system.
- **Delete Courses**: This application can delete courses within the source system.
- **Create Terms**: This application can create terms from the source system.
- **Read Terms**: This application can read terms from the source system.
- **Update Terms**: This application can update terms from the source system.
- **Delete Terms**: This application can delete terms from the source system.

### Application Permissions for Users
- **Read Profile**: This application can read the profile of the current user.
- **Update Profile**: This application can update the profile of the current user.
- **Read Courses**: This application can read the courses of the current user.
- **Read Course Rosters**: This application can read the course rosters of the current user, if the user is a teacher.
- **Create Resources**: This application can create course resources for the current user, if the user is a teacher.
- **Read Resources**: This application can view course resources for the current user.
- **Update Resources**: This application can update course resources for the current user, if the user is a teacher.
- **Delete Resources**: This application can delete course resources for the current user, if the user is a teacher.
- **Create Submissions**: This application can create assignment submissions for the current user, if the user is a student.
- **Read Submissions**: This application can read assignment submissions for the current user.
- **Update Submissions**: This application can update assignment submissions for the current user, if the user is a student.
- **Delete Submissions**: This application can delete assignment submissions for the current user.
- **Read Grades**: This application can read assignment grades for the current user.
- **Update Grades**: This application can update assignment grades in courses where the user is a teacher.
