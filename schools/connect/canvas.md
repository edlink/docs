<div class="card notice alert">
    <p>
        If you already have an Edlink Administrator account, and have already connected your Canvas to at least one
        partner application, you should skip directly to the final step, entitled "Complete the Integration".
    </p>
</div>

Integrating with Canvas is a breeze for school administrators, and should take about 5 minutes. This guide
details the steps required to get a Canvas integration up and running. Once Canvas is connected, you will have control over
the groups of people and the functionality that partner applications have access to. For any future applications you'd like to authorize,
you **do not** need to repeat these steps.

When you connect your district Canvas to one of our partners, you can expect the following functionality (it may vary depending on the permissions
that you grant):

- Students, teachers, and administrators will be able to sign into approved applications with their Canvas account.
- Approved applications can sync course roster information from Canvas.
- Approved applications can create and update coursework within Canvas courses.
- Approved applications can sync grades directly into Canvas.

## Confirm That You're a Canvas Administrator

Completing the Canvas integration process requires a Canvas Administrator. Confirming that you have administrative access is a simple. Canvas administrators
will have an "Admin" tab on their left-hand sidebar. If you do not have an Admin tab, similar to the picture below, then you will not be able to complete this
process. Please reach out to the appropriate technology admin at your school or university and have them complete these steps instead.
<img class="block framed" src="https://edlink.github.io/docs/media/administrators/canvas-admin.png" width="500" alt="Canvas Administrator Tab" />

## Create Canvas Developer Keys

Edlink connects through the Canvas API to provide seamless experiences for teacher and students. In order to do so, you need to generate
developer keys (even when you wish to leverage Edlink's LTI capabilities). Here are the steps required to create developer keys:

1. Log into your school or university Canvas account.
2. Navigate to your Admin tab for the top-level site by clicking the `Admin` tab and then the name of your organization.
3. Click the `Developer Keys` menu item towards the bottom left-hand side.
4. Create a new developer key by clicking the `+ Developer Key` button and then select the `+ API Key` option from the dropdown.
5. Fill out the form with the following details (all other fields should remain blank):
<div class="card selectable-fields">
    <label>Key Name</label>
    <input type="text" readonly value="Edlink" />
    <label>Owner Email</label>
    <input type="text" readonly value="support@ed.link" />
    <label>Redirect URIs</label>
    <textarea readonly>https://ed.link/api/authentication/canvas&#13;https://ed.link/sso/administrator</textarea>
    <label>Icon URL</label>
    <input type="text" readonly value="https://ed.link/icon.png" />
</div>
6. Click the blue `Save` button in the bottom right-hand side of the screen.
7. Toggle the `State` switch to "ON" next to the developer key that you just created.

<img class="block" src="https://edlink.github.io/docs/media/administrators/canvas-key-state.png" alt="Connect G Suite to Edlink" />

You're all done and ready to move on to the final step.

## Complete the Integration

This step lets our system know that you want to connect your Canvas and grant access to one of our partner applications. The integration flow is throughly documented
elsewhere, so this section will focus only on the step where you connect your Canvas district. When you get to the `Sources` page, select "Canvas" from the dropdown.
You will see the following form:
<img class="block framed" src="https://edlink.github.io/docs/media/administrators/canvas-connect.png" width="400" alt="Connect Canvas to Edlink" />

1. **Source Nickname** - Create a nickname that your students and teachers will recognize. This name can be something like "Canvas" or "My School's Canvas". It does not have to be anything in particular, but it should be familiar to your users.
2. **Canvas Domain** The domain that you visit when you want to access Canvas. Typically, this will be something like `https://myschool.instructure.com` or `https://canvas.myschool.edu`.
3. **Developer Key ID** - Copy and paste the Developer Key that we created during the step above.
4. **Developer Key Secret** - Copy and paste the Developer Key Secret that we created during the step above. You can find it by clicking the "Show Key" button, below the other key. Please be careful that you copy the *entire* secret. Any missing characters will result in an inability for Edlink to connect. It is extremely important that you do not share this secret key with anyone else.
5. **Administrator Account** - This is the final step and ensures that you have completed everything else successfully.
    1. Click the `Connect` button on the right side of the box.
    2. Log into your Canvas account. You may already be logged in, in which case, skip to the next step.
    3. Canvas will prompt you to authorize Edlink. Click the blue "Authorize" button.
    4. Upon authorization, Canvas will send you back to Edlink and the box will change to say "Account Connected".
<img class="block" src="https://edlink.github.io/docs/media/administrators/canvas-admin-connected.png" width="500" alt="Canvas Account Connected" />

If you are having trouble connecting, there is probably an error with your Canvas configuration. Most likely, you either incorrectly entered your school's Canvas domain, or improperly copied over the Developer Key / Secret. If you are still having trouble, don't hesitate to [contact us](/support) for more assistance.

You are now finished and can click the black "Connect Source" button at the bottom of the screen.