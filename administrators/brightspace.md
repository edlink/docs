<div class="card notice alert">
    <p>
        If you already have an Edlink Administrator account, and have already connected your Brightspace to at least one
        partner application, you should skip directly to the final step, entitled "Complete the Integration".
    </p>
</div>

Integrating with Brightspace is a breeze for school administrators, and should take about 5 minutes. This guide
details the steps required to get a Brightspace integration up and running. Once Brightspace is connected, you will have control over the groups of people and the functionality that partner applications have access to. For any future applications you'd like to authorize, you **do not** need to repeat these steps.

When you connect your district Brightspace to one of our partners, you can expect the following functionality (it may vary depending on the permissions that you grant):

- Students, teachers, and administrators will be able to sign into approved applications with their Brightspace account.
- Approved applications can sync course roster information from Brightspace.
- Approved applications can create and update coursework within Brightspace courses.
- Approved applications can sync grades directly into Brightspace.

## Confirm That You're a Brightspace Administrator

Completing the Brightspace integration process requires a Brightspace Administrator. Confirming that you have administrative access is a simple. Brightspace administrators will have an "Manage Extensibility" option in their settings menu. If you do not see this page, indicated in the picture below, then you will not be able to complete this
process. Please reach out to the appropriate technology admin at your school or university and have them complete these steps instead.

<img class="block framed" src="/documentation/media/administrators/brightspace-administrator.png" alt="Brightspace Administrator Tab" />

## Register a New Application

Edlink connects through the Brightspace API to provide seamless experiences for teacher and students. In order to do so, you need to register a new application (even when you wish to leverage Edlink's LTI capabilities). Here are the steps required to do so:

1. Log into your school or university Brightspace account.
2. Navigate to the `Manage Extensibility` page by clicking on the option in the settings menu.
3. Click the `OAuth 2.0` tab and then select the blue button to `Register an App`.
4. Fill out the form with the following details (all other fields should remain blank):
<div class="card selectable-fields">
    <label>Application Name</label>
    <input type="text" readonly value="Edlink" />
    <label>Redirect URI</label>
    <input type="text" readonly value="https://ed.link/api/authentication/brightspace" />
    <label>Scope</label>
    <textarea readonly>organizations:organization:read content:completions:read,write content:modules:read content:toc:read content:topics:read,write core:*:* enrollment:orgunit:read grades:*:* role:detail:* users:userdata:read</textarea>
    <label>Prompt For User Consent</label>
    <input type="text" readonly value="False (Uncheck this box)" />
    <label>Enable Refresh Tokens</label>
    <input type="text" readonly value="True (Check this box)" />
    <label>Non-commercial Developer</label>
    <input type="text" readonly value="True (Check this box)" />
</div>
6. Click `Register` to complete the process.

You're all done and ready to move on to the final step.

## Complete the Integration

This step lets our system know that you want to connect your Brightspace and grant access to one of our partner applications. The integration flow is throughly documented
elsewhere, so this section will focus only on the step where you connect your Brightspace district. When you get to the `Sources` page, select "Brightspace" from the dropdown.
You will see the following form:
<img class="block framed" src="/documentation/media/administrators/brightspace-configuration.png" width="400" alt="Connect Brightspace to Edlink" />

1. **Source Nickname** - Create a nickname that your students and teachers will recognize. This name can be something like "Brightspace" or "My School's Brightspace". It does not have to be anything in particular, but it should be familiar to your users.
2. **Brightspace Domain** The domain that you visit when you want to access Brightspace. Typically, this will be something like `https://myschool.brightspace.com` or `https://brightspace.myschool.edu`.
3. **Client ID** - Copy and paste the Client ID that we created during the step above.
4. **Client Secret** - Copy and paste the Client Secret that we created during the step above. Please be careful that you copy the *entire* secret. Any missing characters will result in an inability for Edlink to connect. It is extremely important that you do not share this secret key with anyone else.
5. **Administrator Account** - This is the final step and ensures that you have completed everything else successfully.
    1. Click the `Connect` button on the right side of the box.
    2. Log into your Brightspace account. You may already be logged in, in which case, skip to the next step.
    3. Brightspace may prompt you to authorize Edlink. Click the blue "Authorize" button.
    4. Upon authorization, Brightspace will send you back to Edlink and the box will change to say "Account Connected".

If you are having trouble connecting, there is probably an error with your Brightspace configuration. Most likely, you either incorrectly entered your school's Brightspace domain, or improperly copied over the Developer Key / Secret. If you are still having trouble, don't hesitate to [contact us](/support) for more assistance.

You are now finished and can click the black "Connect Source" button at the bottom of the screen.