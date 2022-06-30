Edlink integrates with the following LMS, SIS, and data providers (collectively known as “data platforms”):
- Canvas
- Schoology
- Google Classroom
- Microsoft Teams
- Moodle
- Blackboard
- Brightspace
- Clever
- Classlink
- PowerSchool

##For how long does Edlink retain data?
Edlink will only access and retain specific data from a school’s data platform if it has been connected by a school technology administrator. Edlink gives granular control to the school and third-parties to ensure only the required data is shared and accessed. The data is frequently updated to ensure that Edlink only retains up-to-date data. If a record is removed from within the data platform it will be removed from Edlink during the next sync. Additionally, Edlink retains data backups for 7 days, and retains audit logs for up to 30 days.

##Can a school ask Edlink to remove all of their stored data?
Yes, school admins can request that Edlink remove all associated data. Edlink will also inform any third-party that they will no longer be able to access the school’s data through Edlink. In this event, all audit logs will be immediately deleted, however we may retain backups for up to 7 days.

##Where is the data stored?
Edlink stores school data within DigitalOcean. DigitalOcean has received the EU-U.S. and Swiss-U.S. Privacy Shield Certification. This demonstrates their compliance with the EU-U.S. and Swiss-U.S. Privacy Shield Frameworks as set forth by the U.S. Department of Commerce and the European Commission. The framework provides DigitalOcean a mechanism to comply with data protection requirements when transferring personal data from the European Union and Switzerland to the United States. Data of Edlink users located in the UK, EU, or Switzerland are maintained in the DigitalOcean FRA1 data center. DigitalOcean also holds the ISO/IEC 27001:2013 Certification for complying with the globally recognized information security controls framework.

##How is the data secured?

####Data encryption
Data is encrypted during transit and at rest using DigitalOceans's managed database encryption service and our own SSL certificates. The database is encrypted using the LUKS cipher, which is an industry standard. In transit, data is encrypted using RSA 256.

####Access Control
All database access between Edlink and DigitalOcean is protected by a secure password and IP limitations. A strong password policy is always in place. Two factor authentication is required for all accounts that have access to school data or administrational functionality. Staff only have access to the minimum amount of data required to perform their job.

####Data Scopes
Third-parties define the scope of data required for their application within Edlink. These scopes can be defined down to a granular level (i.e. first name) which is approved by the school. An application is not able to access data outside of the agreed scope without further school approval.

##DigitalOcean Deletions Policy
Information relating to the deletions policy for DigitalOcean and additional GDPR compliance can be found at https://www.digitalocean.com/legal/gdpr-faq/.

##Does Edlink have a signed agreement with each third-party application?
Yes Edlink has a signed license agreement with every third-party application that uses Edlink services for data platform integrations.

##Can schools have visibility of the data a third-party is requesting?
Yes, schools have visibility and control of the data they share with third-parties via the Edlink dashboard. School administrators can also request audit logs of requests made by third-parties.

##What information does Edlink extract?
Edlink extracts information including: the people, courses, schools, enrollments, and semesters (terms) contained within a Data Platform. The personal information that Edlink stores will vary by system, but may include: First name, middle name, last name, email address, profile picture, birthday, gender, phone number, locale (language preference), and role within your organization (e.g. teacher or student).

##How often does Edlink extract data from data platforms?
Edlink extracts data from a school’s data platform on a regular basis. By default updates occur multiple times per day, although the schedule can be tailored to the schools requirements.

##Who has access to the data?
Edlink developers and client management staff have access to school data for troubleshooting and issue resolution purposes only. All staff undergo training and follow company policies to ensure the security and confidentiality of school data.

##Does Edlink use any third-parties who have access to the data?
Only third-parties who have been approved by a school administrator have direct access to data. No other third-party is permitted to access the school’s data.

##Can schools request an individual's data to not be extracted from their data platform?
Yes, Edlink can block the data of any individual who does not want Edlink to store or pass on their data to a third-party. Requests can be made by emailing privacy@ed.link.

##Will any data be transferred outside of the EEA?
Edlink schools located in the EU, UK, or Switzerland will be assigned to a data center based in the EU (Frankfurt, Germany). This EU data center maintains all needed Edlink application and data servers and will only be transferred to third-party applications outside the EU with specific permissions from school administrators.

##Can schools control what data is available to third-parties?

####Revoking access
Schools can revoke access to a third-party with immediate effect. Revoking access to a third-party takes place within the Edlink dashboard.

####Approving data scopes
Schools will be notified when a third-party requests access to their data or changes to existing data scopes. Schools will be required to approve (from inside the Edlink dashboard), the scopes before the third-party is granted access to the data.

####Optional data scopes
The third-party outlines the data scopes they require as a minimum to run their application. Third-parties can also define optional data scopes to access data that adds additional value or functionality to their application. Schools have the ability to approve these optional data scopes during the approval process or at a point in the future.

##What software will be installed?
Typically, no software will be necessary to install to enable integrations with school data platforms. However, we do require schools that use Moodle to install an open-source Moodle plugin to connect to Edlink.

##What actions are Edlink taking with regards to the GDPR?
Edlink has reviewed policies, procedures and infrastructure to ensure they are in line with the General Data Protection Regulation (GDPR). Edlink is committed to compliance with all relevant EU and Member State laws in respect of personal data, and the protection of the rights and freedoms of individuals whose information we collect and process in accordance with the General Data Protection Regulation (GDPR).

##Additional documentation
Please visit https://ed.link/docs/legal/terms for additional information.

If you require any further information please email privacy@ed.link.
