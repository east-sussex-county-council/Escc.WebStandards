# East Sussex County Council web standards

These standards apply to web pages produced by or for East Sussex County Council or partnerships that include East Sussex County Council. This includes intranet and extranet pages and web applications. These standards should be read in conjunction with other relevant documents listed in the text.

Where further information is required, please [contact the Communications team](https://apps.eastsussex.gov.uk/contactus/emailus/feedback.aspx).
 
We are providing a public service, and it must be fully available to everyone. Pages should be functional, interesting and attractive – in that order.

The residents of East Sussex are a disparate group. It is important that our pages are easy for everyone to use, including those who aren’t used to the web, who have disabilities which affect their use of the web, or who don’t have English as a first language. 

## The East Sussex County Council brand

Our brand includes the logo, wave pattern, font, colours and photos. All web pages and applications produced for East Sussex County Council must use our corporate brand. Our brand guidelines are available on our intranet (for staff), or by contacting the Communications team.  

Our [house style](https://www.eastsussex.gov.uk/about-this-site/housestyle/) sets out how you should phrase and punctuate text. It includes preferred spellings, alternative words, advice on plain English and making printed documents available online. 

Wherever possible, new developments should be branded as part of an existing East Sussex County Council website, not as a new, separate website. Any exception to this must be agreed with the Head of Digital and Design Services.
 
## Browser compatibility

To find out which browsers to support, please refer to the [GOV.UK policy for browsers and devices](https://www.gov.uk/service-manual/technology/designing-for-different-browsers-and-devices). You must also support all browsers in common use at East Sussex County Council. The IT & Digital service can provide statistics showing which browsers are installed, but at the time of writing this means Internet Explorer 11 and Google Chrome.

All websites must use a responsive design that supports all screen sizes from a typical mobile phone up to desktop screens.

## Accessibility

Websites must comply with W3C [Web Content Accessibility Guidelines 2.0](http://www.w3.org/TR/WCAG20/) at the level required by UK central government. At the time of writing this is WCAG 2.0 level AA.   

All public sector organisations have an [Equality Duty](https://www.equalityhumanrights.com/en/advice-and-guidance/public-sector-equality-duty) to “promote equality of opportunity for disabled people”. If any project cannot meet WCAG 2.0 at the relevant level this must be signed off by the Web Services Manager and the Legal Services team.

## JavaScript

Where JavaScript is used, it is essential that the page remains accessible. In the first instance, make sure all features are usable with just a keyboard. See the [Techniques for the Web Content Accessibility Guidelines 2.0](http://www.w3.org/TR/WCAG20-TECHS/) for more recommendations.

JavaScript runs in the user’s browser, which is an unpredictable environment. To mitigate this:

*	Adopt a [progressive enhancement](https://en.wikipedia.org/wiki/Progressive_enhancement) approach. 
*	Use feature detection to avoid attempting to use unsupported features.
*	JavaScript must not interfere with other scripts used on the page. Minimise use of the global namespace and avoid inline event handlers.
*	If JavaScript fails, it should fail silently. Users should not be presented with error messages.	

Our preferred JavaScript framework is [JQuery](http://jquery.com/) and it is available by default in all pages on [www.eastsussex.gov.uk](https://www.eastsussex.gov.uk). Our preferred testing framework is [Chutzpah](https://github.com/mmanela/chutzpah) running [Mocha](http://mochajs.org/). 


## Server-side development

Websites should run on Windows with IIS.

Our preferred server-side technology is ASP.NET MVC. Where source code is provided it should be written in C#. Use NuGet for dependency management (we have a private feed when packages can be hosted if required). Our preferrred testing framework is [NUnit](http://www.nunit.org/).

Our preferred database is Microsoft SQL Server.

All public-facing applications should have uptime-monitoring configured using [Azure Application Insights](https://azure.microsoft.com/en-us/services/application-insights/). Contact our Communications team to get this set up.

Applications developed for internal use at East Sussex County Council should use Microsoft Active Directory for authentication. Users logged into our network should not be asked to sign in again.

Our preferred content management system is [Umbraco](https://umbraco.com/). We also use [WordPress.org](https://en-gb.wordpress.org/).

## Security

All websites must use TLS 1.2 with a SHA256 certificate (or better) throughout, and specify an [HSTS header](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security). Where possible the HTTP protocol should not be supported at all. Otherwise it should redirect all requests immediately to HTTPS.

We strongly recommend the use of a restrictive [Content Security Policy](https://content-security-policy.com/) which whitelists only the origins required for specific resources. CSS and JavaScript should be loaded from a separate URL, or if that is not possible it should use a nonce. `unsafe-inline` permissions should be granted only in exceptional circumstances where a non-compliant third-party component is deemed essential to the page.

Our [Escc.Web.SecurityConfig](https://github.com/east-sussex-county-council/Escc.Web.SecurityConfig) NuGet package can be used to apply recommended headers to an ASP.NET application.

Public-facing websites owned and managed by East Sussex County Council are subject to regular penetration testing. All applications must take measures to protect against common threats including, but not limited to, SQL injection attacks, cross-site scripting, session hijacking and account enumeration.

## Analytics

All websites should use Google Analytics, which should be configured to send data to [our Google Analytics account](https://data.gov.uk/dataset/east-sussex-county-council-web-analytics). Please contact the Communications team to set up a new property in Google Analytics. Do not set up a separate Google Analytics account.

In addition to standard Google Analytics tracking, clicks on documents and external links should be tracked. The recommended approach for doing this is to implement the code in [Escc.js](https://github.com/east-sussex-county-council/Escc.js).

All websites should also be verified in [Google Search Console](https://www.google.com/webmasters/tools/) using the Communications team's Google account.

## Unicode

Pages should be encoded in UTF-8 Unicode text. This should be specified in the HTTP headers:

	Content-Type: text/html; charset=utf-8

and in the metadata of the page:

	<meta charset="UTF-8" />

Where a page contains foreign-language text, this must be Unicode text with the correct language identified in the HTML using the `lang` and `xml:lang` attributes. Images of foreign-language text are not an acceptable alternative.

## Links

Links [should be underlined](http://www.useit.com/alertbox/20040510.html) except where the links are part of a graphical element such as a button or menu. Visited links should appear differently to unvisited links.
 
[Do not open links in new windows](http://www.smashingmagazine.com/2008/07/01/should-links-open-in-new-windows/) and avoid pop-ups and modal dialogs, which can confuse or irritate users and are often blocked by browsers. [Links to documents should open in new windows](http://www.useit.com/alertbox/open_new_windows.html), but you should notify the user that this will happen. You can use the code in [Escc.js](https://github.com/east-sussex-county-council/Escc.js) to enable configure this correctly.

[Links to anchors within the same page can be confusing](https://www.nngroup.com/articles/in-page-links/) only where their different behaviour is made clear and adds significant value.

## Video

Videos should be hosted on [our YouTube channel](https://www.youtube.com/user/EastSussexCC). They may be unlisted videos if they are not intended for the public. If a video contains sensitive content which must not be publicly accessible please discuss your requirements with our Communications team.

## Downloadable documents

CSV (for simple documents) or Excel (for more complex needs) are the preferred formats for numeric data. For other downloadable documents Adobe PDF is the preferred format. RTF or Microsoft Word are acceptable alternatives. 

The PDF format is intended for print, not for viewing on the web, so it should be used when you expect a document to be printed, not as a shortcut to styling content. PDF documents must be optimised for the screen, have Fast Web View enabled, and be [tagged with information about the document structure for accessibility](http://www.adobe.com/uk/accessibility/products/acrobat/training.html). 

Where downloadable documents are displayed, the file size should be shown. Links to downloadable documents should open in a new window (see Links).