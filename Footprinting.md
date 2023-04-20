# Search Engines Footprint
## Google Hacking Techniques
- Learn detailed google techniques on [this link](https://www.googleguide.com).
- For google advance search, can also visit this link - [https://www.google.co.in/advanced_search](https://www.google.co.in/advanced_search).
- For google advance image search, can also visit this link - [https://www.google.co.in/advanced_image_search](https://www.google.co.in/advanced_image_search).
- For google reverse image search, can also visit this link - [https://www.google.co.in/imghp](https://www.google.co.in/imghp).
![](images/20221118111202.png)
![](images/20221118111302.png)  
![](images/20221118111451.png)
![](images/20221118111801.png)

## Other Search Tools and Techniques
![](images/20221118111912.png)
To Search Video metadata, we can use
- [Youtube Metadata](https://mattw.io/youtube-metadata/)

## Other Search Engines
### Meta Search
Meta search engines are a different type of search engines that use other search engines (Google, Bing, Ask.com, etc.) to produce their own results from the Internet in a very short time span.

Using meta search engines, such as Startpage, MetaGer, and eTools.ch, attackers can send multiple search queries to several search engines simultaneously and gather substantially detailed information such as information from shopping sites (Amazon, eBay, etc.), images, videos, biogs, news, and articles from different sources. Further, meta search engines also provide privacy to the search engine user by hiding the user's IP address.

### FTP Search
Using FTP search engines such as NAPALM FTP Indexer, FreewareWeb FTP File Search, and Globalfilesearch.com, attackers can search for critical files and directories containing valuable information such as business strategies, tax documents, personal employee records, financial records, licensed software, and other confidential information.

![](images/20221118115246.png)  

### loT Search Engines
With the help of loT search engines such as Shodan, Censys, and Thingful, attackers can obtain information such as the manufacturer details, geographical location, IP address, hostname, and open ports of the target loT device. Using this information, the attacker can establish a back door to the loT devices and gain access to them to launch further attacks.

# Finding a Company's Top-Level Domains (TLDs) and Sub-domains

## Use google dorks
We can use following dork to get all subdomains -

```site:microsoft . com -inurl:www```

## Using Netcraft
Source: https://www.netcraft.com

## Using Pentest-Tools
Source: https://pentest-tools.com

## Using Sudomy
It is a python tool and is very effective in finding all subdomains.

# People Search
## theHarvestor
Attackers use theHarvester tool to perform enumeration on Linked In and find employees of the target company along with their job titles.

## Job Sites
Job sites are benificial for searching about a person in detail.

# Determining the Operating System
Attackers use various online tools such as Netcraft, Shodan, and Censys to detect the operating system used at the target organization.

## Netcraft
The technique of obtaining information about the target network operating system is called OS fingerprinting. Open https://www.netcraft.com/tools/ in the browser and type the URL of the target website in the What's that site running? field. Attackers use the Netcraft tool to identify all the sites associated with the target domain along with the operating system running at each site.

## SHODAN Search Engine
Shodan is a computer search engine that searches the Internet for connected devices (routers, servers, and loT.}. You can use Shodan to discover which devices are connected to the Internet, where they are located, and who is using them.

## Censys
Source: https://censys.io

Censys monitors the infrastructure and discovers unknown assets anywhere on the Internet. It provides a full view of every server and device exposed to the Internet

# VoIP and VPN Footprinting through SHODAN

Shodan is a search engine that enables attackers to perform footprinting at various levels. It is used to detect devices and networks with vulnerabilities. A search in Shodan for VoIP and VPN footprinting can deliver various results, which will help gather VPN- and VoIP-related information.

# Public Source-Code Repositories
Source code-based repositories are on line services or tools available on internal servers or can be hosted on third-party websites such as GitHub, GitLab, SourceForge, and BitBucket. These sites contain sensitive data related to configuration files, private Secure Shell (SSH) and Secure Sockets Layer (SSL) keys, source-code files, dynamic libraries, and software tools developed by contributors, which can be leveraged by attackers to launch attacks on the target organization.

## Recon-ng
Source: https://github.com

Recon-ng is a full-featured reconnaissance framework designed to provide a powerful environment to conduct web-based reconnaissance quickly and thoroughly. It assists attackers in gathering information from public source-code repositories.

# Social Networking Sites
![](images/20221121121748.png)  

## BuzzSumo
Source: https://buzzsumo.com

BuzzSumo's advanced social search engine finds the most shared content for a topic, author, or domain. It shows the shared activity across all the major social networks including Twitter, Facebook, Linked In, Google Plus, and Pinterest.

# Information Resources Sites
## EDGAR Database
Source: https://www.sec.gov/edgar.shtml
## D&B Hoovers
Source: https://www.dnb.com
## LexisNexis
Source: https://www.lexisnexis.com
## Business Wire
Source: https://www.businesswire.com
## Factiva
Source: https;//www.dowjones.com
# Information Resources Sites - What Are the Company's Plans?
## MarketWatch
Source: https;//www.marketwatch.com
## The Wall Street Transcript
Source: https;//www.twst.com
## Euromonitor
Source: https://www.euromonitor.com
## Experian
Source: https://www.experian.com
## The Search Monitor
Source: https://www.thesearchmonitor.com
## USPTO
Source: https://www.uspto.gov
# Competitive Intelligence - What Expert Opinions Say About the Company? 
## SEMRush
Source: https://www.semrush.com
## ABI/INFORM Global
Source: https:j /www.proquest.com
## SimilarWeb
Source: https://www.similarweb.com
## SERanking
Source: https://seranking.com
# Gathering Information from Financial Services
Google Finance
Source: https://www.google.com/finance
# Gathering Information from Business Profile Sites
Attackers use business profile sites such as opencorporates, Crunchbase, and corporationwiki to gather important information about the target organizations, such as their location, addresses, contact information (such as phone numbers, email addresses), employee database, department names, type of service provided, and type of industry.
# Monitoring Targets Using Alerts
## Google Alerts
Source: https://www.google.com/alerts

Google Alerts automatically notifies users when new content from news, websites, biogs, videos, and/or discussion groups matches a set of search terms selected by the user and stored by the Google Alerts service.
# Tracking the Online Reputation of the Target
Online reputation tracking tools help us to discover what people are saying online about the company's brand in real time across the web, social media, and news. They help in monitoring, measuring, and managing one's reputation online.

An attacker may use ORM tracking tools to:
-	Track a company's online reputation
-	Collect a company's search engine ranking information
-	Obtain email notifications when a company is mentioned on line
-	Track conversations
-	Obtain social news about the target organization

## Mention 
Source: https://mention.com 
# Gathering Information from Groups, Forums, and Biogs
Attackers can register with fake profiles in Google Groups, Yahoo!Groups, and so on. They try to join the target organization's employee groups, where they can obtain personal and company information. Attackers can also search for information in groups, forums, and biogs by Fully Qualified Domain Names (FQDNs), IP addresses, and usernames.

# Gathering Information from NNTP Usenet Newsgroups
A Usenet newsgroup is a repository of notes or messages on various subjects and topics that are submitted by users over the Internet. The Network News Transfer Protocol (NNTP) is used to relay Usenet news articles from discussions over the newsgroup. Usenet newsgroups can be a useful source of valuable information about a target. Many professionals seek help on Usenet newsgroups by posting questions and asking for solutions. To obtain solutions to these issues, they sometimes post more detailed information about the target than needed. Attackers can search Usenet newsgroups or mailing lists such as Newshosting, Eweka, and Supernews to find valuable information about the operating systems {OSes), software, web servers, etc. used by the target organization.

# Gathering Information from Public Source-Code Repositories
Source code-based repositories are online services or tools available on internal servers or can be hosted on third-party websites such as GitHub, GitLab, SourceForge, and BitBucket. These sites contain sensitive data related to configuration files, private Secure Shell (SSH) and Secure Sockets Layer (SSL) keys, source-code files, dynamic libraries, and software tools developed by contributors, which can be leveraged by attackers to launch attacks on the target organization.

## Recon-ng
Source: https://github.com

# General Resources for Locating Information from Social Media Sites 
- Attackers track social media sites using BuzzSumo, Google Trend, Hashatit, etc. to discover most shared content using hashtags or keywords, track accounts and URLs, email addresses, etc. 
- Attackers use this information to perform phishing, social engineering, and other types of attacks 
- BuzzSumo's advanced social search engine finds the most shared content for a topic, author or a domain 

## BuzzSumo
Source: https://buzzsumo.com 

# Conducting Location Search on Social Media Sites 
Attackers use on line tools, such as Followerwonk, Hootsuite, and Meltwater, to search for both geotagged and non-geotagged information about the target on social media sites.

# Constructing and Analyzing Social Network Graphs 
- The construction of social network graphs involves representing various connections and relationships between people in the form of graphs to analyze and extract valuable information from various social networking connections 
- Using graphical analysis, attackers can identify how a group of users communicate, what information they share, and their personal and professional interests 
- Attackers use tools such as Gephi, SocNetV, and NodeXL to construct and analyze social networks and obtain critical information about the target organization/users.

# Tools for Footprinting through Social Networking Sites
Attackers use various tools such as Sherlock, Social Searcher, and UserRecon to footprint social networking sites such as Twitter, lnstagram, Facebook, and Pinterest to gather sensitive information about the target such as the date of birth, educational qualification, employment status, name of relatives, and information about the organization that they are working for, including the business strategy, potential clients, and upcoming project plans. 

# Website Footprinting
Browsing the target website may provide the following information: 
- Software used and its version 
- Operating system used and its scripting platform & Sub-directories and parameters 
- Filename, path, database field name, or query 
- Technologies used 
- Contact and CMS details 
## Burp Suite 
Source: https://portswigger.net 
## Website Footprinting using Web Spiders 
A web spider (also known as web crawler or web robot) is a program or automated script that
browses websites in a methodical manner to collect specific information such as employee names
and email addresses. Attackers then use the collected information to perform footprinting and
social engineering attacks. Web spidering fails if the target website has the robots.txt file in its
root directory with a listing of directories to prevent crawling.
Attackers can uncover all the files and web pages on the target website by simply feeding the
web spider with a URL. Then, the web spider sends hundreds of requests to the target website
and analyzes the HTML code of all the received responses for identifying additional links. If any
new links are found, then the spider adds them to the target list and starts spidering and
analyzing the newly discovered links. This method helps attackers to not only detect exploitable
web-attack surfaces but also to find all the directories, web pages, and files that make up the
target website.
## Web Data Extractor
Source: http://www.webextractor.com
## Website Mirroring Tool: HTTrack Web Site Copier
Source: https://www.httrack.com
## Extracting Website Information from https://archive.org
Source: https://archive.org
Attackers can use tools such as Photon to retrieve archived URLs of the target website from
archive.erg. 
## photon.py
Run the following command to retrieve the archive.erg links of the target website:

`python photon.py -u <URL of the Target Website> -1 3 -t 200 --wayback`
Run the following command to retrieve archived UR Ls of the target website:

`python photon.py -u <URL of the Target Website> - 1 3 -t 200 -only-urls`
## Octoparse
Source: https://www.octoparse.com

Octoparse offers automatic data extraction, as it quickly scrapes web data without
coding and turns web pages into structured data. As shown in the screenshot,
attackers use Octoparse to captu re information from webpages, such as t ext, links,
image URLs, or html code.

# Gathering the Word list from the Target Website
The words available on the target website may reveal critical information that helps
attackers to perform further exploitation. Attackers gather a list of email addresses
related to the target organization using various search engines, social networking sites,
web spidering tools, etc. After obtaining these email addresses, an attacker can gather a
list of words available on the target website. This information helps the attacker to
perform brute-force attacks on the target organization. An attacker uses the CeWL tool
to gather a list of words from the target website and perform a brute-force attack on the
email addresses gathered earlier.
## cewl
`cewl --help`

This command displays various options that a user can use to obtain a list of words from the target website.

`cewl www.certifiedhacker.com`

This command returns a list of unique words present in the target URL.


# Extracting Metadata of Public Documents
Useful information may reside on the target organization's website in the form of pdf
documents, Microsoft Word files, and other files in various formats. Attackers extract
valuable data, including metadata and hidden information from such documents. The
data mainly contains hidden information about the public documents that can be
analyzed to extract information such as the title of the page, description, keywords,
creation/modification date and time of the content, and usernames and e-mail addresses
of employees of the target organization.
An attacker can misuse this information to perform malicious activities against the target
organization by brute-forcing authentication using the usernames and e-mail addresses
of employees, or perform social engineering to send malware, which can infect the target
system.
## ExifTool
Source: https://exiftool.org
# Web Updates Monitoring Tools
## Website-Watcher
Source: https://www.aignes.com
# Monitoring Website Traffic of the Target Company
Attackers can monitor a target company's website traffic using tools such as Web-Stat,
Rank Tracker, and Team Viewer to collect valuable information. These tools help to collect information about the target's customer base, which help attackers to disguise
themselves as customers and launch social engineering attacks on the target.
The information collected includes:
- Total visitors: Tools such as Cl icky (https://clicky.com) find the total number of visitors
browsing the target website.
- Page views: Tools such as Opentracker (https://www.opentracker.net) monitor the
total number of pages viewed by the users along with the timestamps and the status
of the user on a particular web page (whether the web page is still active or closed).
- Bounce rate: Tools such as Google Analytics (https ://analytics.google.com) measure
the bounce rate of the target company's website.
- Live visitors map: Tools such as Web-Stat (https://www.web-stat.com) track the
geographical location of the users visiting the company's website.
- Site ranking: Tools such as Rank Tracker (https://www.ranktracker.com) track a
company's rank on the web.
- Audience geography: Tools such as Rank Tracker track a company's customer
locations on the globe.
- Track Visitors and monitor sales: Tools such as goingup! (https://goingup.com) track
visitors, monitor sales, and show conversation rates with the company's website.
