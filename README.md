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
  open-company-profile: 1.0,
  lang: "en",
  
  //Basic information 
  name: "Lightbox Holdings Company, Inc.",
  pretty-name: "Lightbox Holdings",
  short-name: "Lightbox",
  description: "Lightbox holdings is the largest manufacturer of widgets and things",
  founded: '2016-03-02',
  hq-address: "4300 Wilson Boulevard\nArlington, VA 22203"
  hq-phone: "(510) 413-7396",
  
  //Identity Information
  identity-cik: "0001106191",
  
  //Links
  link-website: 'http://www.lightboxholding.com',
  link-about-us : "https://www.aetna.com/about-us/aetna-history.html",
  link-contact-us : "http://Aetna.com/about-us/contact-aetna.html",
  link-executives : "https://www.aetna.com/about-us/aetna-leadership.html",
  link-facebook : "https://www.facebook.com/aetna",
  link-glassdoor : "http://www.glassdoor.com/Reviews/Aetna-Reviews-E16.htm",
  link-google-plus : "https://plus.google.com/111685156523506874595/about",
  link-instagram : null,
  link-investor-relations : "http://Aetna.com/about-us/investor-information.html",
  link-jobs : "http://Aetna.com/about-us/aetna-careers.html",
  link-linkedin : "https://www.linkedin.com/company/aetna?trk=top-nav-home",
  link-milestones : "https://www.aetna.com/about-us/investor-information.html",
  link-pinterest : "http://..",
  link-products : "http://..",
  link-tumblr : "http://..",
  link-twitter : "https://twitter.com/aetna",
  link-youtube : "https://www.youtube.com/aetna",
  link-crunchbase: "http://..",
  link-rss-feed: "http://..",
  
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
  
  // Investors
  investors: [
    {
      date: '2015-03-21',
      investor-name: 'ABC Capital',
      invested-amount: 5300000,
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
```
