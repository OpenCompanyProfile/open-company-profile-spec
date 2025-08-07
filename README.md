# Open Company Profile Spec v2.0

The Open Company Profile (OCP) data format is an open standard for the structured exchange of company profile data. Version 2.0 is a complete overhaul of the original spec, designed for better organization, extensibility, and modern use cases.

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

The OCP v2.0 schema is organized into several logical objects:

*   `metadata`: Information about the profile data itself.
*   `companyInfo`: Core details about the company.
*   `onlinePresence`: Links to websites, social media, and other online platforms.
*   `branding`: Logos and other brand assets.
*   `identifiers`: Standardized business identifiers.
*   `keyPersonnel`: Information about important people in the company.
*   `financials`: Data related to the company's financial structure, including securities.

---

### Root Object

| Field      | Type   | Required | Description                               |
| :--------- | :----- | :------- | :---------------------------------------- |
| `metadata` | Object | Yes      | Contains metadata about the profile.      |
| `companyInfo`| Object | Yes      | Contains core information about the company. |
| `onlinePresence`| Object | No       | Links to the company's online presence. |
| `branding` | Object | No       | Brand assets like logos.                  |
| `identifiers`| Object | No       | Business identifiers.                     |
| `keyPersonnel`| Array  | No       | An array of key personnel.                |
| `financials` | Object | No       | Financial information about the company.  |


### `metadata` Object

| Field         | Type   | Required | Description                                                  |
| :------------ | :----- | :------- | :----------------------------------------------------------- |
| `specVersion` | String | Yes      | The version of the OCP spec used (e.g., "2.0").              |
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

---

## Sample OCP v2.0 JSON

```json
{
  "metadata": {
    "specVersion": "2.0",
    "language": "en",
    "lastUpdated": "2025-08-06T21:00:00Z"
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
  "onlinePresence": {
    "links": [
      {
        "type": "website",
        "url": "http://www.lightboxholding.com"
      },
      {
        "type": "twitter",
        "url": "https://twitter.com/lightbox"
      },
      {
        "type": "linkedin",
        "url": "https://www.linkedin.com/company/lightbox"
      },
      {
        "type": "tiktok",
        "url": "https://www.tiktok.com/@lightbox"
      }
    ]
  },
  "branding": {
    "logos": [
      {
        "url": "https://cdn..com/logos/primary.svg",
        "type": "primary",
        "mediaType": "image/svg+xml"
      },
      {
        "url": "https://cdn.lightbox.com/logos/icon.png",
        "type": "icon",
        "mediaType": "image/png"
      }
    ]
  },
  "identifiers": {
    "cik": "0001106191",
    "lei": "5493001B3141F8046B48",
    "duns": "01-234-5678"
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
        ],
        "dividends": [
          {
            "status": "paid",
            "exDate": "2024-11-15",
            "payDate": "2024-12-15",
            "amount": 0.34,
            "currency": "USD"
          },
          {
            "status": "announced",
            "exDate": "2025-02-14",
            "payDate": "2025-03-15",
            "amount": 0.35,
            "currency": "USD"
          }
        ],
        "stockSplits": [
          {
            "date": "2023-06-01",
            "ratio": "2:1"
          }
        ]
      }
    ]
  }
}
```
