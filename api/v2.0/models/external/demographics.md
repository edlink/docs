# Demographics
Additional **Demographics** information for a **[Person](person)**.

## Properties

| Property | Type | Description |
| -------- | ---- | ----------- |
| `birthday` | `date` | The person's birthday! 🎉 |
| `gender` | **[`GenderIdentity`](enums/gender-identity)** | The person's gender. |
| `residence_status` | **[`PublicSchoolResidenceStatus`](enums/public-school-residence-status)** | The person's public school residence status. |
| `english_language_learner` | `boolean` | Whether the person is an English language learner. |
| `country_of_birth` | `string` | Typically an [ISO code for a country](https://ceds.ed.gov/CEDSElementDetails.aspx?TermxTopicId=20002) in which a person was born. |
| `state_of_birth` | `string` | Typically an [abbreviation for the US state name or jurisdiction](https://ceds.ed.gov/CEDSElementDetails.aspx?TermxTopicId=20837) in which a person was born. |
| `city_of_birth` | `string` | The city in which a person was born. |
| `hispanic_or_latino_ethnicity` | `boolean` | The person's hispanic or latino ethnicity status. |
| `races` | **[`Race[]`](enums/race)** | The person's races. |