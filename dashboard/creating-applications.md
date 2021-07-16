Before creating an application, [log into your account](/docs/dashboard/sign-in) and select ***Applications*** in the navigation header. Once there, select **Create Application**. On the *Create Application* page, select the type of application you want to create. Edlink supports the following types of applications:

- **Data Consumer Applications**: Applications which can be authorized by a school to read to write [data from a source](/docs/dashboard/data-sources-dev).
- **Data Connector Applications**: An application that connects two [data sources](/docs/dashboard/data-sources-dev) to [integrate](/docs/dashboard/dev-integrations) the data between them.
- **Service Applications**: An application that can modify your Edlink team. This does not access school data.

![create application](/documentation/media/dashboard/dev/create-application-options.jpg)

After selecting the type of application you wish to create, enter the Name and Description of the application in the appropriate fields. Note that if you are making a **Data Consumer** application, you may also enter the list of valid URIs that you will redirect a user to when your application receives an oAUTH 2.0 token request. When finished, select **Create Application**. This will bring you to the *Application Overview* page.

From the *Application Overview* page, you may access the following menus to let you manage your application:

- [***Keys***](/docs/dashboard/application-keys) ***&*** [***Permissions***](/docs/dashboard/application-permissions-dev): View your Application ID and Secret Key. Also edit the permissions you want your users to have when accessing your application and select which data sources are valid.
- [***Webhooks***](/docs/dashboard/application-webhooks): View your webhook signing secret and determine which endpoints will receive webhook requests. Also select which webhook events you want to receive.
- [***Integrations***](/docs/dashboard/dev-integrations): View the list of organizations that are currently using your application.
- [***Settings***](/docs/dashboard/application-settings): View and edit descriptive information about your application. You may also choose to [destroy your application](/docs/dashboard/destroying-application).
