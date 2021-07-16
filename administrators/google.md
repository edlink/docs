<div class="card notice alert">
    <p>
        If you already have an Edlink Administrator account, and have already connected your G Suite to at least one
        partner application, you should skip directly to the final step, entitled "Complete the Integration".
    </p>
</div>

Integrating with Google G Suite is a breeze for school administrators, and should take less than 5 minutes. This guide
details the steps required to get G Suite integration up and running. Once G Suite is connected, you will have control over
the groups of people and the functionality that partner applications have access to. For any future applications you'd like to authorize,
you **do not** need to repeat these steps.

When you connect your G Suite to one of our partners, you can expect the following functionality (it may vary depending on the permissions
that you grant):

- Students, teachers, and administrators will be able to sign into approved applications with their Google email address and password.
- Approved applications can sync course roster information from Google Classroom courses.
- Approved applications can create and update coursework within Google Classroom courses.
- Approved applications can sync grades directly into Google Classroom.

## Confirm That You're a G Suite Administrator

Completing the G Suite integration process requires a Google Administrator. Confirming that you have administrative access is a simple process.
To do so, simply try to visit the [Google Admin Console](https://admin.google.com). If you are an administrator, you will see a page that looks like this:
<img class="block framed" src="/documentation/media/administrators/g-suite-console.png" alt="G Suite Admin Console Error" />

If you do not have admin access, you will see the following error page:
<img class="block framed" src="/documentation/media/administrators/g-suite-admin-error.png" width="500" alt="G Suite Admin Console Error" />
Once you have confirmed that you are an administrator, you may proceed to the next step.

## Whitelist the Edlink Application

Whitelisting Edlink within G Suite ensures that all teachers and students are able to sign in, and that Edlink has the correct permissions.
Whitelisting Edlink is required for G Suite integrations. Here are the steps required to whitelist Edlink:

1. Visit the [App Access Control](https://admin.google.com/u/0/ac/owl/list?tab=apps) page on the Google Admin Console by clicking the link.
2. Double check that you are signed into the correct Google account by clicking your profile picture in the top right.
3. Click the "Add App" dropdown next to the "Connected apps" header towards the left side of the screen. Select the first option "OAuth App Name Or Client ID".
4. Paste the following Client ID into the search box and click "Search":

<div class="card center monospace code-snippet">
    563820043496-o65vgllud5rrstbf8tg0rltlm5pbg868.apps.googleusercontent.com
</div>

5. Edlink should appear as the only search result. Click the select bubble next to the Edlink logo.
6. Click "Add" in the bottom right of the pop-up.

You're all done and ready to move on to the final step.

<img class="block framed" src="/documentation/media/administrators/g-suite-client-id.png" width="500" alt="G Suite Admin Client ID Pop Up" />

## Complete the Integration

This step lets our system know that you want to connect your G Suite and grant access to one of our partner applications. The integration flow is throughly documented
elsewhere, so this section will focus only on the step where you connect your G Suite. When you get to the `Sources` page, select "Google" from the dropdown.
You will see the following form:
<img class="block framed" src="/documentation/media/administrators/g-suite-connect.png" width="400" alt="Connect G Suite to Edlink" />

1. **Source Nickname** - Create a nickname that your students and teachers will recognize. This name can be something like "Google Classroom" or "My School G Suite". It does not have to be anything in particular, but it should be familiar to your users.
2. **Administrator Account** - This is the final step and connects the application we just whitelisted to your Edlink account.
    1. Click the `Connect` button on the right side of the box.
    2. Choose the correct Google Account. It **must** match the one you used earlier to whitelist Edlink.
    3. Review the permissions and click the blue "Allow" button at the bottom of the page. Teachers and students will not see the same permissions requested that you see as the admin.
<img class="block" src="/documentation/media/administrators/g-suite-admin-connected.png" width="500" alt="G Suite Account Connected" />

You are now finished and can click the black "Connect Source" button at the bottom of the screen.