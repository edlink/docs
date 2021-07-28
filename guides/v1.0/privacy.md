# Privacy

> This document contains a summary of some of our data privacy practices and information. You can find our full legal [Terms & Conditions](../../legal/terms) and [Privacy Policy](../../legal/privacy), as well as a number of additional legal disclosures in the Legal Documents section.

Edlink takes user data privacy extremely seriously. We give school administrators several tools and controls to keep student data safe and secure. These processes and controls also limit unnecessary exposure to developers. We have written at length about the importance of privacy in the [Edlink Community](https://ed.link/community/privacy).

## Requests

* All requests to the API must be sent via HTTPS.
* Edlink will redirect all incoming requests on port 80 (HTTP) to port 443 (HTTPS).
* All requests (except for API metadata) require the inclusion of an Edlink secret key so we can identify the application who is accessing it.
* Extremely detailed data access logs are available to school administrators for auditing.
* Data logs are stored for 7 days, after which they are completely destroyed.
* When data is deleted from our system it is truly deleted, not simply "marked as deleted".

## Encryption

* Edlink data is stored in a managed Google Cloud Platform database.
* Access is restricted to only our production servers, which are located in the same region.
* All data is encrypted in transit, and at rest, via the LUKS encryption specification.
* All data is backed up daily, with a 7 day retention policy, after which it is destroyed completely.

## Legal Requirements

* Edlink is fully FERPA and COPPA compliant.
* Edlink is fully GDPR compliant.
* We honor right-to-forget requests to the best of our ability.
    * Users can email privacy@ed.link to retrieve or destroy their personal data.
    * This may require school administrator consent.
