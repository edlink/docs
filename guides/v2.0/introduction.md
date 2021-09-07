# Introduction

Our RESTful Edlink API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. The purpose of this API is to enable developers of educational software to quickly connect to a variety of school data sources in order to provide a smooth workflow for teachers, students, and administrators.

Edlink data connections create an instant bi-directional data flow between your platform and the school's LMS, SIS, or related system. By drawing information from, and sending information to the LMS, developers can build rich experiences that fit seamlessly into existing classroom environments, with virtually no setup time on the part of the teacher or administrator.

We strive to support as many data sources and standards as possible. By doing the heavy-lifting up front, we can provide our partners with integration capabilities that are far beyond what any given standard can currently provide. Currently, we are compatible with various API, LTI, and OneRoster implementations.

## Graph API Overview

The Graph API enables you to access information at the school or district level. All requests are made with a district-level access token. For example, when you make a call to retrieve a list of people, the list will contain all people at the district. This differs from the User Data API, which you can read about below.

* The Graph API provides access to bulk school data through a single set of endpoints.
* The Graph API connects to a variety of school data sources, such as the school's LMS, SIS, etc.
* The Graph API is bi-directional and can retrieve data as well as post data to school systems.
* The Graph API can limit your exposure to unnecessary or sensitive student data through Sharing Rules.

## User Data API Overview

The User Data API enables you to add single sign on, rostering, content, and gradebook integration with school data sources. All requests documented in this section are scoped to the authenticated user. For example, when you make a call to retrieve a list of courses, you will receive a list of courses in which the requesting user is enrolled. You **will not** receive a list of all courses within an entire school or district.

> Version 2.0 of the Edlink User API will be available in Fall 2021.

* The User Data API provides access to information relating to the user who is currently sign in to your application.
* The API is bi-directional which allows you to perform functions like syncing grades or submitting assignments.
* Sharing Rules apply here, so you will not see data that you are not allowed to access.

## Meta API Overview

The Meta API enables you to access the inner workings of the Edlink dashboard.

> Version 2.0 of the Edlink Meta API will be available in Fall 2021.

* The Meta API provides access to information relating to your Edlink team, applications, and integrations.
* The API is bi-directional, which allows you to perform functions like creating applications.

