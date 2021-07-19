<div class="card notice alert">
    <p>
        If you already have an Edlink Administrator account, and have already connected your Moodle instance to at least one
        partner application, you should skip directly to the final step, entitled "Complete the Integration".
    </p>
</div>

Integrating with Moodle is a breeze for school administrators, and should take about 10 minutes. This guide
details the steps required to get Moodle integration up and running. Once Moodle is connected, you will have control over
the groups of people and the functionality that partner applications have access to. For any future applications you'd like to authorize,
you **do not** need to repeat these steps.

When you connect your Moodle to one of our partners, you can expect the following functionality (it may vary depending on the permissions
that you grant):

- Students, teachers, and administrators will be able to sign into approved applications with their Moodle account.
- Approved applications can sync course roster information from Moodle courses.
- Approved applications can create and update coursework within Moodle courses.
- Approved applications can sync grades directly into Moodle.

## Confirm That You're a Moodle Administrator

In order to continue with the setup process, you must be a Moodle administrator. Figuring out whether or not you have the required permissions is pretty simple: You will need to have the ability to install Moodle plugins. To confirm this, you must first navigate to the "Site Administration" page. If you do not see this tab in your right-hand sidebar, then you are not a site administrator.

<img class="block framed" src="https://edlink.github.io/docs/media/administrators/moodle-site-administration.png" alt="Moodle Site Administration Tab" />

Once on the site administration page, navigate to the plugin settings section by clicking on the "Plugins" tab. The first link under this section will bring you to the "Install Plugins" page. If you do not see this link then you will not have the permissions required to complete this process.

<img class="block framed" src="https://edlink.github.io/docs/media/administrators/moodle-plugin-installation.png" alt="Moodle Plugin Installation Page" />

## Installing the Edlink Moodle Plugin

Edlink connects to Moodle via a custom plugin, designed to supplement the functionality of the Moodle Webservices API. The plugin is easy to install and contains security features to protect data in the event of a security breach.

<div class="flex flex-center">
    <a class="card flex flex-align download-link" href="https://edlink.github.io/docs/media/administrators/edlink.zip" target="_blank">
        <div class="download-icon"></div>
        <div class="ff">
            Download the Edlink Moodle Plugin
        </div>
    </a>
</div>

On the Install Plugins page, drag and drop the Edlink Plugin ZIP file into the upload area. Complete the steps that Moodle requires in order to install the plugin. Once the plugin is installed, you will need to navigate to the Edlink Settings page. It will be located at `https://yourmoodlesite.com/local/edlink/index.php`. You can also find this page by navigating to `Site Administration` > `Server` > `Edlink Settings`.

On the Edlink settings page, click "Generate Edlink API Keys" and a new key pair will be created. Make note of these keys as they will be used later. **Do not, under any circumstances, share these keys with anyone else. They are extremely sensitive. If you believe that your keys have become compromised, please contact us immediately.**

## Complete the Integration

This step lets our system know that you want to connect your Moodle instance. The integration flow is throughly documented
elsewhere, so this section will focus only on the step where you actually configure Moodle. When you get to the `Sources` page, select "Moodle" from the dropdown.
You will see the following form:
<img class="block framed" src="https://edlink.github.io/docs/media/administrators/moodle-configuration.png" width="400" alt="Connect Moodle to Edlink" />

1. **Source Nickname** - Create a nickname that your students and teachers will recognize. It does not have to be anything in particular, but it should be familiar to your users.
2. **Moodle Domain** - The domain that you visit when you want to access Moodle. Typically, this will be something like `https://moodle.myschool.edu`.
3. **Client ID** - Copy and paste the Client ID that we created during the step above.
4. **Client Secret** - Copy and paste the Client Secret that we created during the step above.
3. **Administrator Account** - This is the final step and confirms that all of the information you entered is correct. Click the `Connect` button on the right side of the box and Moodle will redirect you back to Edlink. The box will change to say "Account Connected".

You are now finished and can click the black "Connect Source" button at the bottom of the screen.