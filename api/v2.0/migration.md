# Migration from v1.0

So, you're thinking about making the move to our API V2.0— congratulations!

## Additions

With a new major version comes new features. You may want to look over these and see how they could be useful to your product.

### Results Filtering

We've added a new system to filter results in your API v2.0 requests. Please
review [our guide on filtering results](../../guides/v2.0/filtering-results) for an in-depth look.

### Courses Data Type

We've added a new **[Course](models/external/course)** data type.

A **Course** is a plan of study. Most of the time, many **[Classes](models/external/class)**
of a single **Course** are taught in the same **[Session](models/external/session)**.

For example, a school offers a Data Structures & Algorithms **Course**. There might be
several **[Classes](models/external/class)** of that course, each with a different teacher and a different set of students enrolled in it.

You might imagine that a **Course** would be found in your university's course listing, whereas
a **[Class](models/external/class)** or **[Section](models/external/section)** would be what you
actually **[Enrolled](models/external/enrollment)** in during the class registration period.

### Agents Data Type

We've added a new **[Agent](models/external/agent)** data type.

An **Agent** describes the relationship between two people, and is typically used to represent a connection between a
student and their parent or guardian. If a data source provides emergency contacts, this is how they are
represented in Edlink.


## Lexical Changes

As you know, naming is one of the most important parts of software development. A good name can be the difference
between frustration and clarity.

We know that name changes can be jarring, but we've done our best to make the transition as smooth as possible. We are confident
you'll find the new names to be more consistent with other education systems.

### Organizations

**[v1.0's Organizations](../v1.0/models/organization)** have been split into several new types in v2.0, based on their former `type` field.

* Organizations of type `district` have become **[Districts](models/external/district)**
* Organizations of type `school` have become **[Schools](models/external/school)**
* Organizations of type `course` have become **[Classes](models/external/class)**
* Organizations of type `section` have become **[Sections](models/external/section)**

As a result of this, V1.0's `/organizations` Graph API endpoints no longer exist. You should replace any calls to these with the corresponding new Graph API endpoints.

### Courses

**[v1.0's Courses](../v1.0/models/course)** have been renamed to **[Classes](models/external/class)** to fall more in
line with industry expectations. The old name **[Course](models/external/course)** has been given a new meaning, described in further detail below.

### Terms
**[v1.0's Terms](../v1.0/models/term)** have been renamed to **[Sessions](models/external/session)** to fall more in
line with industry expectations, and to represent a larger variety of time-span-like objects.

## Data Model Updates

We've made some changes to our data model to improve consistency and clarity.

> You can view [our full guide on the V2.0 School Data Model here](/docs/guides/v2.0/external-data-model).

* People may now have more than one `role`. The `role` field has been replaced by `roles`.
* Enrollments are now only made between a Person and a Class. They may optionally include a reference to a Section.
* People now store a reference to their district and zero or more schools. This replaces the old style of using Enrollments to indicate a Person's relationship to a School or District.
* All sources are now forced to have exactly one District.
* All sources are now forced to have at least one School.
* Various enums have new or changed values. All enums now have their values documented in the Models section of the API documentation.

You can [view the complete changelog for more details](changelog).
