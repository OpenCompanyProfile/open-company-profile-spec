# Open Company Profile Spec v2.1

The Open Company Profile (OCP) data format is an open standard for the structured exchange of company profile data. Version 2.1 adds a significant number of fields to provide a more holistic view of a company.

## Guiding Principles

*   **Clarity and Intuition:** The data structure should be easy to understand and use.
*   **Extensibility:** The format should be easy to extend without requiring a new version of the spec for minor additions.
*   **Modernization:** The spec should support current social media platforms and modern data interchange practices.
*   **Machine-Readability:** The format must be strictly machine-readable and adhere to open standards like JSON.

## Data Format

*   Data **must** be formatted as JSON per [RFC 8259](https://tools.ietf.org/html/rfc8259).
*   Files **must** use UTF-8 encoding.
*   The root element **must** be a JSON Object.
*   Field names **should** use camelCase for consistency.

## Schema Overview

The OCP v2.1 schema is organized into several logical objects:

*   `metadata`: Information about the profile data itself.
*   `companyInfo`: Core details about the company.
*   `businessModel`: How the company makes money.
*   `productsAndServices`: The company's products and services.
*   `onlinePresence`: Links to websites, social media, and other online platforms.
*   `branding`: Logos and other brand assets.
*   `identifiers`: Standardized business identifiers.
*   `keyPersonnel`: Information about important people in the company.
*   `financials`: Data related to the company's financial structure, including securities.
*   `eventsAndMilestones`: Company events and milestones.
*   `pressMentions`: Media coverage of the company.
*   `sustainability`: The company's sustainability initiatives.
*   `fundingRounds`: The company's funding history.
*   `marketPresence`: The company's market position.
*   `corporateCulture`: The company's culture and values.
*   `legalAndCompliance`: Legal and compliance information.
*   `community`: The company's community engagement.
*   `intellectualProperty`: The company's intellectual property.
*   `partnerships`: The company's strategic partnerships.


---

### Root Object

| Field      | Type   | Required | Description                               |
| :--------- | :----- | :------- | :---------------------------------------- |
| `metadata` | Object | Yes      | Contains metadata about the profile.      |
| `companyInfo`| Object | Yes      | Contains core information about the company. |
| `businessModel`| Object | No       | How the company makes money. |
| `productsAndServices`| Array | No       | The company's products and services. |
| `onlinePresence`| Object | No       | Links to the company's online presence. |
| `branding` | Object | No       | Brand assets like logos.                  |
| `identifiers`| Object | No       | Business identifiers.                     |
| `keyPersonnel`| Array  | No       | An array of key personnel.                |
| `financials` | Object | No       | Financial information about the company.  |
| `eventsAndMilestones`| Array | No       | Company events and milestones. |
| `pressMentions`| Array | No       | Media coverage of the company. |
| `sustainability`| Object | No       | The company's sustainability initiatives. |
| `fundingRounds`| Array | No       | The company's funding history. |
| `marketPresence`| Object | No       | The company's market position. |
| `corporateCulture`| Object | No       | The company's culture and values. |
| `legalAndCompliance`| Object | No       | Legal and compliance information. |
| `community`| Object | No       | The company's community engagement. |
| `intellectualProperty`| Object | No       | The company's intellectual property. |
| `partnerships`| Array | No       | The company's strategic partnerships. |


### `metadata` Object

| Field         | Type   | Required | Description                                                  |
| :------------ | :----- | :------- | :----------------------------------------------------------- |
| `specVersion` | String | Yes      | The version of the OCP spec used (e.g., "2.1").              |
| `language`    | String | Yes      | The [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) language code for the profile content (e.g., "en"). |
| `lastUpdated` | String | Yes      | The ISO 8601 timestamp of when the profile was last updated. |

### `companyInfo` Object

| Field         | Type   | Required | Description                                                  |
| :------------ | :----- | :------- | :----------------------------------------------------------- |
| `legalName`   | String | Yes      | The official legal name of the company.                      |
| `displayName` | String | No       | A more common or user-friendly name for the company.         |
| `description` | String | Yes      | A brief description of the company and its business.         |
| `foundedDate` | String | No       | The date the company was founded, in ISO 8601 format (YYYY-MM-DD). |
| `address`     | Object | No       | The physical address of the company headquarters.            |

### `address` Object

| Field        | Type   | Description                |
| :----------- | :----- | :------------------------- |
| `street`     | String | Street address.            |
| `city`       | String | City.                      |
| `state`      | String | State, province, or region. |
| `postalCode` | String | Postal or ZIP code.        |
| `country`    | String | Country.                   |

### `businessModel` Object

| Field        | Type   | Description                |
| :----------- | :----- | :------------------------- |
| `primaryRevenueStream`     | String | A string describing the main source of revenue (e.g., "Subscription SaaS", "Direct-to-Consumer Product Sales", "Advertising").            |
| `customerAcquisitionChannels`       | Array | An array of strings listing the primary ways the company acquires customers (e.g., "Organic Search", "Paid Marketing", "Direct Sales Team").                      |

### `productsAndServices` Array Object

| Field        | Type   | Description                |
| :----------- | :----- | :------------------------- |
| `name`     | String | The name of the product or service.            |
| `description`       | String | A short description.                      |
| `category`      | String | A category for the product/service (e.g., "Software", "Hardware", "Consulting"). |
| `url` | String | A link to the product/service page.        |

### `onlinePresence` Object

| Field | Type  | Description                                      |
| :---- | :---- | :----------------------------------------------- |
| `links` | Array | An array of links to the company's online pages. |

### `links` Array Object

| Field | Type   | Description                                                  |
| :---- | :----- | :----------------------------------------------------------- |
| `type`| String | The type of link. Predefined types include: `website`, `blog`, `twitter`, `facebook`, `linkedin`, `instagram`, `youtube`, `tiktok`, `threads`, `github`, `mastodon`, `rss`. Custom types are allowed. |
| `url` | String | The URL for the link.                                        |

### `branding` Object

| Field | Type  | Description                                                  |
| :---- | :---- | :----------------------------------------------------------- |
| `logos`| Array | An array of company logos.                                   |

### `logos` Array Object

| Field | Type   | Description                                                  |
| :---- | :----- | :----------------------------------------------------------- |
| `url` | String | The URL of the logo image file.                              |
| `type`| String | The type of logo (e.g., `primary`, `icon`, `wordmark`).      |
| `mediaType`| String | The IANA media type of the image (e.g., `image/svg+xml`, `image/png`). |

### `identifiers` Object

A key-value map of business identifiers. Keys can include `lei`, `duns`, `cik`, `ticker`, etc.

### `keyPersonnel` Array Object

| Field       | Type   | Description                                      |
| :---------- | :----- | :----------------------------------------------- |
| `name`      | String | Full name of the person.                         |
| `title`     | String | Job title.                                       |
| `biography` | String | A short biography.                               |
| `linkedIn`  | String | A URL to their LinkedIn profile.                 |

### `financials` Object

| Field       | Type  | Description                                                  |
| :---------- | :---- | :----------------------------------------------------------- |
| `securities`| Array | An array of securities issued by the company.                |

### `securities` Array Object

| Field               | Type   | Description                                                  |
| :------------------ | :----- | :----------------------------------------------------------- |
| `type`              | String | The type of security (e.g., `Stock`, `Bond`).                |
| `class`             | String | The class of the security (e.g., `A`, `C`).                  |
| `isin`              | String | The [ISIN](https://en.wikipedia.org/wiki/International_Securities_Identification_Number) for the security. |
| `sharesOutstanding` | Number | The number of shares outstanding.                          |
| `listings`          | Array  | An array of exchange listings for the security.              |
| `dividends`         | Array  | An array of dividend payments.                             |
| `stockSplits`       | Array  | An array of stock split events.                            |

### `listings` Array Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `exchange` | String | The stock exchange where the security is listed (e.g., `NASDAQ`, `LSE`). |
| `symbol` | String | The stock symbol.                                |

### `dividends` Array Object

| Field     | Type   | Description                                                  |
| :-------- | :----- | :----------------------------------------------------------- |
| `status`  | String | The status of the dividend (`announced`, `paid`).             |
| `exDate`  | String | The ex-dividend date in ISO 8601 format.                     |
| `payDate` | String | The payment date in ISO 8601 format.                         |
| `amount`  | Number | The dividend amount per share.                               |
| `currency`| String | The currency of the dividend (e.g., `USD`).                  |

### `stockSplits` Array Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `date`   | String | The date of the split in ISO 8601 format.        |
| `ratio`  | String | The split ratio (e.g., "2:1", "1:5").            |

### `eventsAndMilestones` Array Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `type`   | String | "milestone" or "event".        |
| `title`  | String | The title of the event or milestone.            |
| `date`   | String | The date of the event or milestone in ISO 8601 format. |
| `description` | String | A description of the event or milestone. |
| `url`    | String | A URL for more information. |

### `pressMentions` Array Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `publication` | String | The name of the publication. |
| `title`  | String | The title of the article. |
| `url`    | String | A URL to the article. |
| `date`   | String | The date of the article in ISO 8601 format. |

### `sustainability` Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `esgRating` | String | The company's ESG rating. |
| `certifications` | Array | An array of strings with the names of any sustainability certifications. |
| `reportUrl` | String | A link to the company's sustainability report. |

### `fundingRounds` Array Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `series` | String | The funding series (e.g., "Seed", "Series A"). |
| `leadInvestors` | Array | An array of strings with the names of the lead investors. |
| `amountRaised` | Number | The amount raised in the round. |
| `date`   | String | The date of the funding round in ISO 8601 format. |

### `marketPresence` Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `competitors` | Array | An array of strings with the names of key competitors. |
| `targetAudience` | String | A string describing the primary customer profile. |
| `geographicReach` | String | A string describing the regions where the company operates (e.g., "Global", "North America", "EU"). |

### `corporateCulture` Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `missionStatement` | String | The company's official mission statement. |
| `visionStatement` | String | The company's vision for the future. |
| `coreValues` | Array | An array of strings representing the company's core values. |
| `diversityAndInclusionUrl` | String | A link to a page detailing their D&I policies and initiatives. |

### `legalAndCompliance` Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `termsOfServiceUrl` | String | Link to the company's terms of service. |
| `privacyPolicyUrl` | String | Link to the company's privacy policy. |
| `licensesAndCertifications` | Array | An array of objects, each with a `name` and `authority` (e.g., `{ "name": "ISO 27001", "authority": "ISO" }`). |

### `community` Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `openSourceContributionsUrl` | String | A link to the company's open source projects or contributions (e.g., a GitHub organization page). |
| `communityForumsUrl` | String | A link to official community forums or discussion boards. |
| `socialImpactInitiatives` | Array | An array of objects detailing any philanthropic or social impact work, with a `name`, `description`, and `url`. |

### `intellectualProperty` Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `patents` | Array | An array of patent numbers or links to patent filings. |
| `trademarks` | Array | An array of registered trademark names. |

### `partnerships` Array Object

| Field    | Type   | Description                                      |
| :------- | :----- | :----------------------------------------------- |
| `partnerName` | String | The name of the partner company. |
| `partnershipType` | String | The nature of the partnership (e.g., "Technology Partner", "Channel Partner", "Joint Venture"). |
| `url` | String | A link to a press release or announcement about the partnership. |

---

## Sample OCP v2.1 JSON

```json
{
  "metadata": {
    "specVersion": "2.1",
    "language": "en",
    "lastUpdated": "2025-08-06T21:09:00Z"
  },
  "companyInfo": {
    "legalName": "Lightbox Holdings Company, Inc.",
    "displayName": "Lightbox Holdings",
    "description": "Lightbox Holdings is the largest manufacturer of widgets and things.",
    "foundedDate": "2016-03-02",
    "address": {
      "street": "4300 Wilson Boulevard",
      "city": "Arlington",
      "state": "VA",
      "postalCode": "22203",
      "country": "USA"
    }
  },
  "businessModel": {
    "primaryRevenueStream": "Direct-to-Consumer Product Sales",
    "customerAcquisitionChannels": [
      "Organic Search",
      "Paid Marketing"
    ]
  },
  "productsAndServices": [
    {
      "name": "Widget Pro",
      "description": "The best widget on the market.",
      "category": "Hardware",
      "url": "https://www.lightboxholding.com/widget-pro"
    }
  ],
  "onlinePresence": {
    "links": [
      {
        "type": "website",
        "url": "http://www.lightboxholding.com"
      },
      {
        "type": "twitter",
        "url": "https://twitter.com/lightbox"
      }
    ]
  },
  "branding": {
    "logos": [
      {
        "url": "https://cdn.lightbox.com/logos/primary.svg",
        "type": "primary",
        "mediaType": "image/svg+xml"
      }
    ]
  },
  "identifiers": {
    "cik": "0001106191"
  },
  "keyPersonnel": [
    {
      "name": "John Smith",
      "title": "Chief Executive Officer",
      "biography": "John Smith has been the CEO of Lightbox since its founding in 2016...",
      "linkedIn": "https://www.linkedin.com/in/johnsmith"
    }
  ],
  "financials": {
    "securities": [
      {
        "type": "Stock",
        "class": "C",
        "isin": "US38259P5089",
        "sharesOutstanding": 1056789,
        "listings": [
          {
            "exchange": "NASDAQ",
            "symbol": "LBOX"
          }
        ]
      }
    ]
  },
  "eventsAndMilestones": [
    {
      "type": "milestone",
      "title": "Launched Widget Pro",
      "date": "2022-01-01",
      "description": "We launched our flagship product, the Widget Pro.",
      "url": "https://www.lightboxholding.com/news/widget-pro-launch"
    }
  ],
  "pressMentions": [
    {
      "publication": "TechCrunch",
      "title": "Lightbox's Widget Pro is a game-changer",
      "url": "https://techcrunch.com/2022/01/01/lightbox-widget-pro",
      "date": "2022-01-01"
    }
  ],
  "sustainability": {
    "esgRating": "A",
    "certifications": [
      "B Corp"
    ],
    "reportUrl": "https://www.lightboxholding.com/sustainability"
  },
  "fundingRounds": [
    {
      "series": "Series A",
      "leadInvestors": [
        "VC Firm"
      ],
      "amountRaised": 10000000,
      "date": "2018-01-01"
    }
  ],
  "marketPresence": {
    "competitors": [
      "WidgetCo",
      "Thingamajig Inc."
    ],
    "targetAudience": "Consumers and small businesses",
    "geographicReach": "Global"
  },
  "corporateCulture": {
    "missionStatement": "To make the best widgets in the world.",
    "visionStatement": "A widget on every desk.",
    "coreValues": [
      "Innovation",
      "Quality",
      "Customer Focus"
    ],
    "diversityAndInclusionUrl": "https://www.lightboxholding.com/diversity"
  },
  "legalAndCompliance": {
    "termsOfServiceUrl": "https://www.lightboxholding.com/terms",
    "privacyPolicyUrl": "https://www.lightboxholding.com/privacy",
    "licensesAndCertifications": [
      {
        "name": "ISO 9001",
        "authority": "ISO"
      }
    ]
  },
  "community": {
    "openSourceContributionsUrl": "https://github.com/lightbox",
    "communityForumsUrl": "https://community.lightboxholding.com",
    "socialImpactInitiatives": [
      {
        "name": "Widget for a Cause",
        "description": "We donate a widget for every 100 sold.",
        "url": "https://www.lightboxholding.com/wfac"
      }
    ]
  },
  "intellectualProperty": {
    "trademarks": [
      "Widget Pro"
    ]
  },
  "partnerships": [
    {
      "partnerName": "RetailCo",
      "partnershipType": "Channel Partner",
      "url": "https://www.lightboxholding.com/news/retailco-partnership"
    }
  ]
}
```
