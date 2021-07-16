<div class="card notice alert">
    <p>
        If you already have an Edlink Administrator account, and have already connected your Blackboard to at least one
        partner application, you should skip directly to the final step, entitled "Complete the Integration".
    </p>
</div>

Integrating with Blackboard is a breeze for school administrators, and should take about 5 minutes. This guide
details the steps required to get a Blackboard integration up and running. Once Blackboard is connected, you will have control over the groups of people and the functionality that partner applications have access to. For any future applications you'd like to authorize, you **do not** need to repeat these steps.

When you connect your district Blackboard to one of our partners, you can expect the following functionality (it may vary depending on the permissions
that you grant):

- Students, teachers, and administrators will be able to sign into approved applications with their Blackboard account.
- Approved applications can sync course roster information from Blackboard.
- Approved applications can create and update coursework within Blackboard courses.
- Approved applications can sync grades directly into Blackboard.

## Confirm That You're a Blackboard Administrator

Completing the Blackboard integration process requires a Blackboard Administrator. Confirming that you have administrative access is a simple. Blackboard administrators will have a `System Admin` tab on their top navigation bar. If you do not have a `System Admin` tab, similar to the picture below, then you will not be able to complete this process. Please reach out to the appropriate technology admin at your school or university and have them complete these steps instead.
<img class="block framed" src="/documentation/media/administrators/blackboard-administrator.png" alt="Blackboard System Admin Tab" />

## Add Edlink as a REST API Connection

Edlink connects through the Blackboard API to provide seamless experiences for teacher and students. In order to do so, you need to add Edlink as a REST API connection (even when you wish to leverage Edlink's LTI capabilities). Here are the steps required to do so:

1. Log into your school or university Blackboard account.
2. Navigate to your System Admin tab by clicking `System Admin` in the top-right banner.
3. Under the `Integrations` block, click on `REST API Integrations`.
4. Click `Create Integration` in the top-left. The button may be slightly difficult to see depending on your organization's custom styles.
5. Fill out the fields as follows:
    * `Application ID` - Paste in the Edlink Application ID from the input field below.
    * `Learn User` - Use your own account or create a new one, this field is irrelevant when `End User Access` is selected.
    * `End User Access` - Set to "Yes". This field is important and allows your teachers and students to make use of this integration.
    * `Authorized To Act As User` - Set to "Yes". This allows Edlink to make requests on the user's behalf where applicable (e.g. submitting an assignment).
6. Click the `Submit` button in the bottom-right to proceed.

<div class="card selectable-fields">
    <label>Application ID</label>
    <input type="text" readonly value="db1de065-8d3a-4641-9b2b-e3d8b5fbd92a" />
</div>

You're all done and ready to move on to the final step.

## Complete the Integration

This step lets our system know that you want to connect your Blackboard and grant access to one of our partner applications. The integration flow is throughly documented
elsewhere, so this section will focus only on the step where you connect your Blackboard district. When you get to the `Sources` page, select "Blackboard" from the dropdown.
You will see the following form:
<img class="block framed" src="/documentation/media/administrators/blackboard-connect.png" width="400" alt="Connect Blackboard to Edlink" />

1. **Source Nickname** - Create a nickname that your students and teachers will recognize. This name can be something like "Blackboard" or "My School's Blackboard". It does not have to be anything in particular, but it should be familiar to your users.
2. **Blackboard Domain** The domain that you visit when you want to access Blackboard. Typically, this will be something like `https://myschool.blackboard.com` or `https://blackboard.myschool.edu`.
3. **Administrator Account** - This is the final step and ensures that you have completed everything else successfully.
    1. Click the `Connect` button on the right side of the box.
    2. Log into your Blackboard account. You may already be logged in, in which case, skip to the next step.
    3. Blackboard will prompt you to authorize Edlink. Click the authorize button if you are prompted.
    4. Upon authorization, Blackboard will send you back to Edlink and the box will change to say "Account Connected".

If you are having trouble connecting, there is probably an error with your Blackboard configuration. Most likely, you either incorrectly entered your school's Blackboard domain, or improperly added Edlink as a REST API provider in Blackboard. If you are still having trouble, don't hesitate to [contact us](/support) for more assistance.

You are now finished and can click the black "Connect Source" button at the bottom of the screen.