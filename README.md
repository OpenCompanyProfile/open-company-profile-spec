# Open Company Profile Spec
The Open Company Profile data format is an open format for the structured exchange of company profile data between different organizations

http://www.opencompanyprofile.com/

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
  openCompanyProfileVersion: 1.0,
  lang: "en",
  
  //Basic information 
  name: "Lightbox Holdings Company, Inc.",
  prettyName: "Lightbox Holdings",
  shortName: "Lightbox",
  description: "Lightbox holdings is the largest manufacturer of widgets and things",
  founded: '2016-03-02',
  hqAddress: "4300 Wilson Boulevard\nArlington, VA 22203"
  hqPhone: "(510) 413-7396",
  
  //Identity Information
  cikId: "0001106191",
  prconnectId: "PRC0905A",
  
  //Links
  links: {
   website: 'http://www.lightboxholding.com',
   aboutUs : "https://www.aetna.com/about-us/aetna-history.html",
   contactUs : "http://Aetna.com/about-us/contact-aetna.html",
   executives : "https://www.aetna.com/about-us/aetna-leadership.html",
   facebook : "https://www.facebook.com/aetna",
   glassdoor : "http://www.glassdoor.com/Reviews/Aetna-Reviews-E16.htm",
   googlePlus : "https://plus.google.com/111685156523506874595/about",
   instagram : null,
   investorRelations : "http://Aetna.com/about-us/investor-information.html",
   jobs : "http://Aetna.com/about-us/aetna-careers.html",
   linkedin : "https://www.linkedin.com/company/aetna?trk=top-nav-home",
   milestones : "https://www.aetna.com/about-us/investor-information.html",
   pinterest : "http://..",
   products : "http://..",
   tumblr : "http://..",
   twitter : "https://twitter.com/aetna",
   youtube : "https://www.youtube.com/aetna",
   owler: "http://..",
   crunchbase: "http://..",
   rssFeed: "http://..",
  },
  //Images
  images: [
    {
      name: "Picture of Lightbox corporate headquarters",
      description: "Lightbox has the largest headquarters in North America",
      src: "http://my.site/hq.png",
      link: "http://my.site/dest.html",
    },
  ],
  
  //Videos
  videos: [
    {
      name: "Our Products",
      description: "Check out this YouTube video where we show off all of our cool products",
      src: "http://my.site/foo.mp4",
      link: "http://my.site/dest.html",
    }
  ],
  
  // Investments
  investments: [
    {
      date: '2015-03-21',
      name: 'ABC Capital',
      amount: 5300000,
      currency: 'usd',
    }
  ],
  
  // Executives
  executives: [
    {
      name: 'John Smith',
      title: 'CEO',
      born: '1974-03-19',
      biography: "Mr. Joshua L. Peirez is President, Chief Operating Officer of The Dun & Bradstreet Corporation. Mr. Peirez previously served as President, Global Product, Marketing and Innovation from June 2011 to February 2014 and President, Innovation and Chief Marketing Officer from September 2010 to May 2011. Before joining Dun & Bradstreet, Mr. Peirez spent 10 years with MasterCard, most recently as Chief Innovation Officer for MasterCard Worldwide from January 2009 to August 2010. Prior to that, Mr. Peirez served as Chief Payment System Integrity Officer for MasterCard from April 2007 to January 2009 and as Group Executive, Global Public Policy and Associate General Counsel from May 2002 to April 2007. He also served as Counsel and Secretary to MasterCard's U.S. Region Advisory Board of Directors from May 2002 to December 2006."
    }
  ]
  
  structure: "Company",
  domicile: {
    country: "USA",
    state: "California",
  },
  securities: [
    {
      type: 'Stock',
      class: 'C',
      description: "Common Shares",
      currency: 'usd',
      sharesOutstanding: 1056789,
      sharesFloat: 1057894,
      isin: 'US38259P5089',
      listings: [
        {
          exchange: 'Nasdaq',
          symbol: 'LBOX',
        },
        {
          exchange: 'LSE',
          symbol: 'LIGHT',
        }
      ],
      futureDividends: [
        {
          payable: '2016-05-03',
          announced: '2016-04-15',
          executed: '2016-06-01',
          payout: 0.34,
          currency: 'usd',
          futureInterval: 'quarterly',
        }
      ],
      priorDividends: [
        {
          payable: '2016-05-03',
          announced: '2016-04-15',
          executed: '2016-06-01',
          payout: 0.34,
          currency: 'usd',
        }
      ],
      splits: [
        {
          date: '2016-04-17',
          sharesFrom: 5,
          sharesTo: 3.3,
        }
      ]
    }
  ]
}
```
