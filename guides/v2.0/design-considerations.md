# Design Considerations

## Not All Systems are Created Equal

Not every system provides the same breadth or depth of data to Edlink. As such, there are some quirks you might want to take into consideration for your implementation.

### Roles

Not every system gives us the data needed to determine a **[Person](../../api/v2.0/models/external/person)**'s roles. In these cases, `roles` will be an empty array. 

While a person may not have any roles, their **[Enrollments](../../api/v2.0/models/external/enrollment)**  will. However, you shouldn't assume the `role` will be consistent between all of a person's enrollments.

For instance, a person could be a `teacher` in one **[Class](../../api/v2.0/models/external/class)** while being a `student` in another. This occurs most commonly when someone is a `student` in a professional development class, while being a `teacher` in all of their other classes.

### School-less Systems

Some systems do not have a concept of a **[School](../../api/v2.0/models/external/school)**. In these cases, our system will create a fake school called the District Office. All **[Classes](../../api/v2.0/models/external/class)** will belong to this fake school.

## Syncing Data from Edlink

You should ensure your system has a mechanism to do a [full sync](class-rostering) of data from Edlink. This would involve [paginating](paginated-requests) through the data you need for each **[Integration](../../api/v2.0/models/internal/integration)** via our Graph API. 

This is especially important if your primary sync mechanism relies on our [events API](events). In case either system accidentally drops important information (e.g. due to an outage) it's useful to be able to run a full sync to get back to a good state.

A full sync is also the preferred way to retrieve all data from Edlink for a new integration.

## Don't Rely On Email Addresses

**[Click here to read our blog post about why email addresses aren't a good way to match users.](https://ed.link/community/why-you-shouldnt-match-users-by-email-address/)**

**[Click here to read our security guide, which also covers this topic.](security)**

Generally, you should be using a **[Person](../../api/v2.0/models/external/person)**'s `id` field to match users.
