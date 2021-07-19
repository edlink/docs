<div class="card notice alert">
    <p>
        If you already have an Edlink Administrator account, and have already connected your OneRoster-compliant SIS to at least one
        partner application, you should skip directly to the final step, entitled "Complete the Integration".
    </p>
</div>

Integrating with a OneRoster-compliant source is a breeze for school administrators, and should take about 5 minutes. This guide
details the steps required to get a OneRoster integration up and running. Once your source is connected, you will have control over
the groups of people and the functionality that partner applications have access to. For any future applications you'd like to authorize,
you **do not** need to repeat these steps. When you connect your district SIS to one of our partners, the approved application can sync course roster information from the SIS.

You must be a school administrator in order to complete this process.

## Create OneRoster Keys

This process will vary based on the system from which you are trying to import your data. In order to proceed to the next step, you ultimately need three pieces of information:

1. **OneRoster Server URL**
2. **OneRoster Client ID**
3. **OneRoster Client Secret**

## Complete the Integration

This step lets our system know that you want to connect your OneRoster source and grant access to one of our partner applications. The integration flow is throughly documented
elsewhere, so this section will focus only on the step where you connect your SIS. When you get to the `Sources` page, select "OneRoster" from the dropdown.
You will see the following form:

<img class="block framed" src="https://edlink.github.io/docs/media/administrators/oneroster-configuration.png" width="400" alt="Connect Your OneRoster Source to Edlink" />

1. **Source Nickname** - Create a nickname that your students and teachers will recognize. This name can be something like "Canvas" or "My School's Canvas". It does not have to be anything in particular, but it should be familiar to your users.
2. **OneRoster Server URL** The URL that your OneRoster server is located at.
3. **OneRoster Client ID** - Copy and paste the OneRoster Client ID that you created during the step above.
4. **OneRoster Client Secret** - Copy and paste the OneRoster Client Secret that you created during the step above. It is extremely important that you do not share this secret key with anyone else.

If you are having trouble connecting, there is probably an error with your Canvas configuration. Most likely, you either incorrectly entered your school's Canvas domain, or improperly copied over the Developer Key / Secret. If you are still having trouble, don't hesitate to [contact us](/support) for more assistance.

You are now finished and can click the black "Connect Source" button at the bottom of the screen.