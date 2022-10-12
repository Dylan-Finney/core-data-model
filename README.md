<div align="center">
<p float="left">
	<a href="https://www.prifina.com/"><img src="https://www.prifina.com/uploads/1/0/1/4/101493144/prifina-new-logo-big-black_orig.png" alt="Prifina Inc Logo" height="80"><img src="https://www.prifina.com/uploads/1/0/1/4/101493144/prifina-new-logo-big-white_orig.png" alt="Prifina Inc Logo" height="80"></a>
</p>
<h1> Core Data Models</h1>
</div>

## Table of Contents
- [Supported Data Models](#supported-data-models)
	- [Base Data Models](#base-data-models)
		- [Individual](#individual)
		- [IndividualApp](#individualapp)
	- [Components](#components)
		- [Address](#address)	
	- [Enums](#enums)
		- [TempUnits](#temp-units)	
		- [MeasUnits](#meas-units)	
- [Roadmap](#roadmap)
- [Contribute](#contribute)


## Supported Data Models
## Base Data Models
### Individual
User's Personal Data on Prifina - Based on OpenID Connect Basic Client Profile
| Name |Scalar|Description |
|--|--|--|
|sub | String! |Subject - Identifier for the End-User at the Issuer.|
|name| String |End-User's full name in displayable form including all name parts, possibly including titles and suffixes, ordered according to the End-User's locale and preferences.|
|given_name| String |Given name(s) or first name(s) of the End-User. Note that in some cultures, people can have multiple given names; all can be present, with the names being separated by space characters|
|family_name| String |Surname(s) or last name(s) of the End-User. Note that in some cultures, people can have multiple family names or no family name; all can be present, with the names being separated by space characters.|
|middle_name| String |Middle name(s) of the End-User. Note that in some cultures, people can have multiple middle names; all can be present, with the names being separated by space characters. Also note that in some cultures, middle names are not used.|
|nickname| String |Casual name of the End-User that may or may not be the same as the given_name. For instance, a nickname value of Mike might be returned alongside a given_name value of Michael.|
|preferred_username| String |Shorthand name that the End-User wishes to be referred to at the RP, such as janedoe or j.doe. This value MAY be any valid JSON string including special characters such as @, /, or whitespace. This value MUST NOT be relied upon to be unique by the RP.|
|profile| String |URL of the End-User's profile page. The contents of this Web page SHOULD be about the End-User.|
|picture| String |string URL of the End-User's profile picture. This URL MUST refer to an image file (for example, a PNG, JPEG, or GIF image file), rather than to a Web page containing an image. Note that this URL SHOULD specifically reference a profile photo of the End-User suitable for displaying when describing the End-User, rather than an arbitrary photo taken by the End-User.|
|website|String|URL of the End-User's Web page or blog. This Web page SHOULD contain information published by the End-User or an organization that the End-User is affiliated with.|
|email| String |End-User's preferred e-mail address. Its value MUST conform to the RFC 5322 [RFC5322] addr-spec syntax. This value MUST NOT be relied upon to be unique by the RP, as discussed in Section 2.5.3.|
|email_verified| Boolean|True if the End-User's e-mail address has been verified; otherwise false. When this Claim Value is true, this means that the OP took affirmative steps to ensure that this e-mail address was controlled by the End-User at the time the verification was performed. The means by which an e-mail address is verified is context-specific, and dependent upon the trust framework or contractual agreements within which the parties are operating.|
|gender| String |End-User's gender. Values defined by this specification are female and male. Other values MAY be used when neither of the defined values are applicable.|
|birthdate| String |End-User's birthday, represented as an ISO 8601:2004 [ISO8601‑2004] YYYY-MM-DD format. The year MAY be 0000, indicating that it is omitted. To represent only the year, YYYY format is allowed. Note that depending on the underlying platform's date related function, providing just year can result in varying month and day, so the implementers need to take this factor into account to correctly process the dates. |
|zoneinfo| String |String from zoneinfo [zoneinfo] time zone database representing the End-User's time zone. For example, Europe/Paris or America/Los_Angeles.|
|locale_| String |End-User's locale, represented as a BCP47 [RFC5646] language tag. This is typically an ISO 639-1 Alpha-2 [ISO639‑1] language code in lowercase and an ISO 3166-1 Alpha-2 [ISO3166‑1] country code in uppercase, separated by a dash. For example, en-US or fr-CA. As a compatibility note, some implementations have used an underscore as the separator rather than a dash, for example, en_US; Implementations MAY choose to accept this locale syntax as well.|
|phone_number| Boolean|End-User's preferred telephone number. E.164 [E.164] is RECOMMENDED as the format of this Claim, for example, +1 (425) 555-1212 or +56 (2) 687 2400. If the phone number contains an extension, it is RECOMMENDED that the extension be represented using the RFC 3966 [RFC3966] extension syntax, for example, +1 (604) 555-1234;ext=5678.|
|phone_number_verified| Boolean |True if the End-User's phone number has been verified; otherwise false. When this Claim Value is true, this means that the OP took affirmative steps to ensure that this phone number was controlled by the End-User at the time the verification was performed. The means by which a phone number is verified is context-specific, and dependent upon the trust framework or contractual agreements within which the parties are operating. When true, the phone_number Claim MUST be in E.164 format and any extensions MUST be represented in RFC 3966 format.|
|updated_at| Int |Time the End-User's information was last updated. The time is represented as the number of seconds from 1970-01-01T0:0:0Z as measured in UTC until the date/time.|
|address| [Address](#address) |End-User's preferred address. The value of the address member is a JSON [RFC4627] structure containing some or all of the members defined in Section 2.5.1.|
|individualApps| [[IndividualApp!]!](#individualapp)|The collection of user's config and preference data for each app/widget they use|
### IndividualApp
The user's config and preference data for each app/widget they use
| Name |Scalar|Description |
|--|--|--|
|units_preference| [MeasUnits](#meas-units)	|The units the user wish to display data in, e.g. metric, imperial, etc|
|color_scheme | String |The color scheme the user has set for the widget/application|
|language| String |Display Language|
|cookies| Boolean||
|custom| Json|A property to store any and all app/widget specific data that developers wish to store that does not have a dedicated property for|
|personalized_ads| Boolean||
|temperature| [TempUnits](#temp-units)||

## Components
### Address
The data structure behind storing the user's address
| Name |Scalar|Description |
|--|--|--|
|formatted| String |Full mailing address, formatted for display or use on a mailing label. This field MAY contain multiple lines, separated by newline characters.|
|street_address| String |Full street address component, which MAY include house number, street name, Post Office Box, and multi-line extended street address information. This field MAY contain multiple lines, separated by newline characters.|
|locality| String |City or locality component.|
|region| String|State, province, prefecture or region component.|
|country| String|Country name component.|
## Enums
### Temp Units
The units used for the temperature
| Value |
|--|
|Celsius|
|Fahrenheit|

### Meas Units
The units of measurement desired by the user
| Value |
|--|
|Metric|
|Imperial|

## Roadmap

 - Filtering on  Schemas from GitHub need to be implemented
	 - The schemas generated from the graphql library are different from the ones generated by Hygraph
	 - Filtering needs to be universal

## Contribute
### Useful Tools

 - [JSON-to-Simple-GraphQL-Schema](https://walmartlabs.github.io/json-to-simple-graphql-schema/): Converts JSON data into a simple GraphQL Schema. Gives an insightful view at how the models you want added may be created from the data.
 - [Hygraph](https://hygraph.com/): A free CMS that allows for the creation of GraphQL APIs with custom data models and documenting tools. The data models created through this application can be converted into a Schema through other tools, such as Our Website and [GraphQL Playground](https://www.graphqlbin.com/v2/new)
 - [GraphQL Voyager](https://ivangoncharov.github.io/graphql-voyager/): GraphQL Schema Visualizer. Our website makes use of this library. Best to not use Hygraph Schema as it shows a lot of system fields that may not be needed. 
