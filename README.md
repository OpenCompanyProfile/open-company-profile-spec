# Open Company Profile Spec
The Open Company Profile data format is an open format for the structured exchange of company profile data between different organizations

## Conventions
* Any field marked as *must* is required, and needs to be included for the file to be valid
* Any field marked as *may* can be included but is not required for the file to be valid

## Data Format
* Data is to be formatted in JSON format per RFC 7159 (https://tools.ietf.org/html/rfc7159)
* If data is stored in a file, the file *must* use UTF-8 encoding as per RFC 3629 (https://tools.ietf.org/html/rfc3629)
* The root element *must* be an Object
* The root element *must* include the key `open-company-profile`, with the protocol version used as the value
* The root element *must* include the key `lang`, with the language of the profile specified as the value
* A profile is expected to be in a single language - if a profile is available in multiple languages, each profiles should be transmitted in a new file

## Protocol Versions
* The initial version of the protocol is 1.0
* Versions with the same major number should be generally regarded as compatible - for example a version 1.0 file should be parsable by a version 1.5 parser
* Versions that differ by the major number are generally assumed to be incompatible - for example, a version 2.0 file would not be readable by a version 1.3 parser

## Sample Data
```javascript
{
  //Header
  open-company-profile: 1.0,
  lang: "en",
  
  //Basic information 
  name: "Lightbox Holdings Company, Inc.",
  pretty-name: "Lightbox Holdings",
  short-name: "Lightbox",
  description: "Lightbox holdings is the largest manufacturer of widgets and things",
  founded: '2016-03-02',
  
  //Links
  link-website: 'http://www.lightboxholding.com',
  link-investor_relations:
  link-executives:
  link-jobs:
  link-facebook:
  link-twitter:
  link-linkedin:
  link-google-plus:
  link-youtube:
  link-glassdoor:
  link-instagram:
  link-pinterest:
  link-tumblr:
  
  //Images
  images: [
    {
      image-name: "Picture of Lightbox corporate headquarters",
      image-description: "Lightbox has the largest headquarters in North America",
      image-src: "http://my.site/hq.png",
    },
  ],
  //Videos
  videos: [
    {
      video-name: "Our Products",
      video-name: "Check out this YouTube video where we show off all of our cool products",
      link: "http://my.site/foo.mp4",
    }
  ],
  
  org-structure: "Company",
  org-domicile: {
    country: "USA",
    state: "California",
  },
  org-share-types: [
    {
      share-class-code: 'C',
      share-class-description: "Common Shares",
      share-currency: 'usd',
      shares-outstanding: 1056789,
      shares-float: 1057894,
      isin: 'US38259P5089',
      listings: [
        {
          exchange: 'Nasdaq',
          symbol: 'LBOX',
          dividends: [
            {
              payable: '2016-05-03',
              announced: '2016-04-15',
              executed: '2016-06-01',
              payout: 0.34,
              currency: 'usd',
              future-interval: 'quarterly',
            }
          ],
          splits: [
            {
              date: '2016-04-17',
              shares-from: 5,
              shares-to: 3.3,
            }
          ]
        },
        {
          exchange: 'LSE',
          symbol: 'LIGHT',
        }
      ]
    }
  ]
}

