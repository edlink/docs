The Edlink User Data API is organized around REST. Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. The purpose of this API is to enable educational software developers to quickly develop two-way integrations with a variety of school data sources in order to provide a smooth workflow for teachers, students, and administrators.

Edlink data connections create an instant bi-directional data flow between your platform and the school's LMS, SIS, or related system. By drawing information from, and sending information to the LMS, your developers can build rich experiences that fit seamlessly into existing classroom environments, with virtually no setup time on the part of the teacher or administrator.

The User Data API enables you to add single sign on, rostering, content, and gradebook integration with school data sources. All requests documented in this section are scoped to the authenticated user. For example, when you make a call to retrieve a list of courses, you will receive a list of courses in which the requesting user is enrolled. You **will not** receive a list of all courses within an entire school or district.

If you're looking for details on working with bulk school data, please check out the [Edlink Graph API](/docs/graph/introduction).

# Getting Started

## SSO Authentication

We provide a client-side Javascript library to assist you in the user authentication process. The process is virtually identical to the oAuth 2.0 flow and works as follows:

* The user visits your website or native application and navigates (or is directed to) a login page.
* They are presented with several different authentication options - one for each supported LMS or fallback authentication provider.
* The user selects the desired LMS and the Edlink Javascript library launches a popup window.
* Edlink directs the user through the login flow, and returns a temporary token to your client side application.
* The client passes the token to the server, and the server exchanges it with the Edlink API for an oAuth token.

Once your server has a valid Edlink oAuth token, it should be set as a cookie to be used for future requests. With the oAuth token, your platform can begin to make requests to retrieve or send user information from the LMS from the endpoints documented below.

## Making Basic Requests

The first request that your platform will likely make after a user is authenticated is to retrieve the user's personal information. This request will provide details including their name, user type (e.g. teacher), email address (if available), profile picture, organization, and LMS. This information may also be enhanced with details not provided directly by their learning management system.

Another request that you may wish to perform is to retrieve the user's course enrollments. In a simple API call, you can access the most up-to-date information about a user's courses. We do not recommend that you cache these requests, so that your information always remains timely.

## Conclusion

The Edlink LMS API provides a fast and easy way to integrate your learning platform with nearly every major learning management system. Instead of receiving raw student and teacher data on a nightly basis, you are able to interact with the LMS on-the-fly and in a bi-directional manner.
