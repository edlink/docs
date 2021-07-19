Integrating with Schoology is a breeze for school administrators, and should take about 5 minutes. This guide
details the steps required to get a Schoology integration up and running. Once Schoology is connected, you will have control over the groups of people and the functionality that partner applications have access to. For any future applications you'd like to authorize, you **do not** need to repeat these steps.

When you connect your district Schoology to one of our partners, you can expect the following functionality (it may vary depending on the permissions
that you grant):

- Students, teachers, and administrators will be able to sign into approved applications with their Schoology account.
- Approved applications can sync course roster information from Schoology.
- Approved applications can create and update coursework within Schoology courses.
- Approved applications can sync grades directly into Schoology.

## Confirm That You're a Schoology Administrator

Completing the Schoology integration process requires a Schoology Administrator. Confirming that you have administrative access is a simple. Schoology administrators will have a "Tools" tab on their top navigation bar that contains options like "User Management" and "School Management". If you do not have a Tools tab, or it does not contain those options, then you will not be able to complete this process. Please reach out to the appropriate technology admin at your school or university and have them complete these steps instead.

## Configure Your Schoology Integration

This step lets our system know that you want to connect your Schoology and grant access to one of our partner applications. The integration flow is throughly documented
elsewhere, so this section will focus only on the step where you connect your Schoology district. When you get to the `Sources` page, select "Schoology" from the dropdown.
You will see the following form:

1. **Source Nickname** - Create a nickname that your students and teachers will recognize. This name can be something like "Schoology" or "My School's Schoology". It does not have to be anything in particular, but it should be familiar to your users.
2. **Schoology Domain** The domain that you visit when you want to access Schoology. Typically, this will be something like `https://myschool.schoology.com` or `https://schoology.myschool.edu`.
3. **Administrator Account** - This is the final step and ensures that you have completed everything else successfully.
    1. Click the `Connect` button on the right side of the box.
    2. Log into your Schoology account. You may already be logged in, in which case, skip to the next step.
    3. Schoology will prompt you to authorize Edlink. Click the authorize button if you are prompted.
    4. Upon authorization, Schoology will send you back to Edlink and the box will change to say "Account Connected".

If you are having trouble connecting, there is probably an error with your Schoology configuration. Most likely, you either incorrectly entered your school's Schoology domain, or improperly added Edlink as a REST API provider in Schoology. If you are still having trouble, don't hesitate to [contact us](/support) for more assistance.

You are now finished and can click the black "Connect Source" button at the bottom of the screen.