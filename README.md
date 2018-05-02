# East Sussex County Council web standards

These standards apply to web pages produced by or for East Sussex County Council or partnerships that include East Sussex County Council. This includes intranet and extranet pages and web applications. These standards should be read in conjunction with other relevant documents listed in the text.

Each requirement is listed with one of three levels:

* **must** - this is essential
* **should** - this is recommended or preferred, but exceptions are allowed
* **may** - this is a suggestion which you can choose to follow or not

Where further information is required, please [contact the Communications team](https://apps.eastsussex.gov.uk/contactus/emailus/feedback.aspx).

The residents of East Sussex are a disparate group, and we are providing a public service. It is important that our pages are easy for everyone to use, including those who aren’t used to the web, who have disabilities which affect their use of the web, or who don’t have English as a first language. Pages should be functional, interesting and attractive – in that order.

## The East Sussex County Council brand

Our brand includes the logo, wave pattern, font, colours and photos. All web pages and applications produced for East Sussex County Council **must** follow our brand guidelines, unless a separate brand has been agreed as part of the specification. Our brand guidelines are available on our intranet (for staff), or by contacting the Communications team.  

Our [house style](https://www.eastsussex.gov.uk/about-this-site/housestyle/) sets out how you should phrase and punctuate text. It includes preferred spellings, alternative words, advice on plain English and making printed documents available online. Websites for East Sussex County Council **must** use our house style. Partnership websites **should** adopt their own house style which **may** be based on ours. 

Wherever possible, new developments **should** be branded as part of an existing East Sussex County Council website, not as a new, separate website. Any exception to this must be agreed with the Head of Digital and Design Services.
 
## Browser compatibility

Websites **must** support the browsers listed in the [GOV.UK policy for browsers and devices](https://www.gov.uk/service-manual/technology/designing-for-different-browsers-and-devices). You **must** also support all browsers in common use at East Sussex County Council. The IT & Digital service can provide statistics showing which browsers are installed, but at the time of writing this means Internet Explorer 11 and Google Chrome.

All websites **must** use a responsive design that supports all screen sizes from a typical mobile phone up to desktop screens.

## Accessibility

Websites **must** comply with W3C [Web Content Accessibility Guidelines (WCAG)](http://www.w3.org/TR/WCAG/) at level AA. This is required by [EU Directive 2016/2102](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32016L2102), which in turn references [EN 301 549](http://mandate376.standards.eu/standard) which [requires conformance with WCAG 2.0 at level AA](http://mandate376.standards.eu/standard/technical-requirements/wcag-20-conformance-requirements). In addition all UK public sector organisations have an [Equality Duty](https://www.equalityhumanrights.com/en/advice-and-guidance/public-sector-equality-duty) to “promote equality of opportunity for disabled people”. 

EN 301 549 is being updated to reference WCAG 2.1, so we should target that standard now. If any project cannot meet WCAG 2.1 at the relevant level this must be signed off by the Head of Digital and Design Services and the Legal Services team.

## JavaScript

Where JavaScript is used, the website **must** remain accessible. In the first instance, make sure all features are usable with just a keyboard. See [Techniques for the Web Content Accessibility Guidelines 2.1](http://www.w3.org/TR/WCAG20-TECHS/) for more recommendations.

JavaScript runs in the user’s browser, which is an unpredictable environment. To mitigate this your JavaScript **should**:

*	Adopt a [progressive enhancement](https://en.wikipedia.org/wiki/Progressive_enhancement) approach. 
*	Use [feature detection](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection) to avoid attempting to use unsupported features.
*	Take care not to interfere with other scripts used on the page. Minimise use of the global namespace and avoid inline event handlers.
*	Fail silently - users should not be presented with technical error messages.

Websites and applications which will depend on technical support by East Sussex County Council staff **must** use native JavaScript or [JQuery](http://jquery.com/) in preference to other JavaScript frameworks. JQuery is available by default in all pages on [www.eastsussex.gov.uk](https://www.eastsussex.gov.uk) and does not need to be included again when building pages for that site. 

JavaScript unit tests which will be supported by East Sussex County Council staff **should** use [Chutzpah](https://github.com/mmanela/chutzpah) running [Mocha](http://mochajs.org/).

Sites which will be hosted and supported by third parties **may** use other JavaScript frameworks.


## Server-side development

For websites and applications which will be hosted by East Sussex County Council and depend on technical support by East Sussex County Council staff:

*	Websites **must** run on Windows with IIS.
*	Server-side code for websites (except WordPress sites) **must** use ASP.NET MVC. 
*	Where .NET source code is provided it **must** be written in C# and **must** use NuGet for dependency management. We have a private feed where packages can be hosted if required. 
*	Unit tests for .NET source code **should** use [NUnit](http://www.nunit.org/).
*	Databases **should** use Microsoft SQL Server.

Sites which will be hosted and supported by third parties **may** use other technologies. 

For all sites, if a content management system is used, it **should** be either [Umbraco](https://umbraco.com/) or [WordPress.org](https://en-gb.wordpress.org/).

Applications developed for internal use at East Sussex County Council **should** use Microsoft Active Directory for authentication. Users logged into our network should not be asked to sign in again.

## Security

All websites **must** use TLS 1.2 with a SHA256 certificate (or better) throughout. The HTTP protocol **should** be switched off wherever possible. When enabled the HTTP protocol **must** redirect all requests immediately to HTTPS, and the website **should** specify an [HSTS header](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security). 

Websites **should** use a restrictive [Content Security Policy](https://content-security-policy.com/) which whitelists only the origins required for specific resources. `unsafe-inline` permissions **should** be avoided, except in exceptional circumstances where a non-compliant third-party component is deemed essential to the page.

Public-facing websites owned and managed by East Sussex County Council are subject to regular penetration testing. All applications **must** take measures to protect against common threats including, but not limited to, SQL injection attacks, cross-site scripting, session hijacking and account enumeration. Websites **may** use our [Escc.Web.SecurityConfig](https://github.com/east-sussex-county-council/Escc.Web.SecurityConfig) NuGet package as a way to apply recommended headers to an ASP.NET application.

## Analytics and monitoring

Websites **must** use Google Analytics, which **should** be configured to send data to [our Google Analytics account](https://data.gov.uk/dataset/east-sussex-county-council-web-analytics). Please contact the Communications team to set up a new property in Google Analytics. Do not set up a separate Google Analytics account. 

Websites hosted and supported by third parties may require Google Analytics data to be sent to the third party's account. In this case access to the relevant Google Analytics property **must** be granted to the Communications team.

In addition to standard Google Analytics tracking, clicks on documents and external links **should** be tracked. This tracking **may** use the code in [Escc.js](https://github.com/east-sussex-county-council/Escc.js).

All websites **should** be verified in [Google Search Console](https://www.google.com/webmasters/tools/) using the Communications team's Google account.

All public-facing applications **should** have uptime-monitoring configured using [Azure Application Insights](https://azure.microsoft.com/en-us/services/application-insights/). This does not require any configuration by third party suppliers. Contact our Communications team to get this set up. 


## Unicode

Pages **must** be encoded in UTF-8 Unicode text. Specify UTF-8 in the HTTP headers:

	Content-Type: text/html; charset=utf-8

and in the metadata of the page:

	<meta charset="UTF-8" />

Where a page contains foreign-language text, this **must** be Unicode text with the correct language identified in the HTML using the `lang` and `xml:lang` attributes. Images of foreign-language text are not an acceptable alternative.

## <a name="links"></a>Links

Links [**should** be underlined](http://www.useit.com/alertbox/20040510.html), and visited links **must** appear differently to unvisited links, except where the links are part of a graphical element such as a button or menu. 
 
Links **must** [open in the same window](http://www.smashingmagazine.com/2008/07/01/should-links-open-in-new-windows/) except in limited circumstances:

* [Links to documents **should** open in new windows](http://www.useit.com/alertbox/open_new_windows.html), but you **should** notify the user that this will happen. You **may** use the code in [Escc.js](https://github.com/east-sussex-county-council/Escc.js) to configure this correctly.
* Where contextual help is on another page (for example, guidance for completing a form) this **may** be set to open in a new window to avoid losing work in progress.

You **should** avoid pop-ups and modal dialogs, which can confuse or irritate users and are often blocked by browsers. If you do use them they **must** be accessible.

[Links to anchors within the same page can be confusing](https://www.nngroup.com/articles/in-page-links/) and **should** be avoided. If you do use them ensure their different behaviour is made clear and adds significant value.

## Video

Videos **should** be hosted on [our YouTube channel](https://www.youtube.com/user/EastSussexCC). They may be unlisted videos if they are not intended for the public. If a video contains sensitive content which would not be released in response to a Freedom of Information request please discuss your requirements with our Communications team.

## Downloadable documents

For numeric data you **must** use CSV (for simple documents) or Excel (XLSX) (for more complex needs). 

For other downloadable documents you **should** use Adobe PDF. However the PDF format is intended for print, not for viewing on the web, so it should be used when you expect a document to be printed, not as a shortcut to creating web content. PDF documents **should** be optimised for the screen, have Fast Web View enabled, and **must** be [tagged with information about the document structure for accessibility](http://www.adobe.com/uk/accessibility/products/acrobat/training.html).

You **may** use RTF or Microsoft Word as alternatives to Adobe PDF.

Where downloadable documents are displayed, the file size **should** be shown. Links to downloadable documents **should** open in a new window (see [Links](#links)).