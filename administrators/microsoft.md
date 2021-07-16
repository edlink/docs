<div class="card notice alert">
    <p>
        If you already have an Edlink Administrator account, and have already connected your Microsoft Office 365 to at least one partner application, you should skip directly to the final step, entitled "Configure Your Microsoft Office 365 Integration".
    </p>
</div>

Integrating with Microsoft Office 365 and Microsoft Teams is a breeze for school administrators, and should take about 5 minutes. This guide details the steps required to get a Microsoft integration up and running. Once Office 365 is connected, you will have control over the groups of people and the functionality that partner applications have access to. For any future applications you'd like to authorize, you **do not** need to repeat these steps.

When you connect your district Microsoft Office 365 and Microsoft Teams to one of our partners, you can expect the following functionality (it may vary depending on the permissions
that you grant):

- Students, teachers, and administrators will be able to sign into approved applications with their Office 365 account.
- Approved applications can sync course roster information from Microsoft Teams.
- Approved applications can create and update coursework within Microsoft Teams courses.
- Approved applications can sync grades directly into Microsoft Teams.

## Confirm That You're a Microsoft Office 365 Administrator

Completing the Microsoft Office 365 integration process requires a Microsoft Office 365 Administrator. Confirming that you have administrative access is a simple. Microsoft administrators will have access to the Office 365 admin console. If you do not have access to the admin console then you will not be able to complete this process. Please reach out to the appropriate technology admin at your school or university and have them complete these steps instead.

<img class="block framed" src="https://edlink.github.io/docs/media/administrators/microsoft-office-365-admin.png" alt="Microsoft Office 365 Administrator Tab" />

## Configure Your Microsoft Office 365 Integration

This step lets our system know that you want to connect Microsoft to Edlink and grant access to one of our partner applications. The integration flow is throughly documented elsewhere, so this section will focus only on the step where you connect your Microsoft Office 365 account. When you get to the `Sources` page, select "Microsoft" from the dropdown.
You will see the following form:

<img class="block framed" src="https://edlink.github.io/docs/media/administrators/microsoft-configuration.png" alt="Connect Microsoft to Edlink" />

1. **Source Nickname** - Create a nickname that your students and teachers will recognize. This name can be something like "Microsoft Office 365" or "My School's Microsoft Teams". It does not have to be anything in particular, but it should be familiar to your users.
2. **Azure Tenant ID** This property will be set automatically during the next step. It represents the Microsoft ID for your school or university.
3. **Administrator Account** - This is the final step and ensures that you have completed everything else successfully.
    1. Click the `Connect` button on the right side of the box.
    2. Log into your Microsoft Office 365 account. You may already be logged in, in which case, skip to the next step.
    3. Microsoft will prompt you to authorize Edlink. Click the authorize button if you are prompted.
    4. Upon authorization, Microsoft will send you back to Edlink and the box will change to say "Account Connected". You will also notice that the Azure Tenant ID has been filled in for you.

You are now finished and can click the black "Connect Source" button at the bottom of the screen.
