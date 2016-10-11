#Documentation

```
easyscrape {download, run, scrape}
```

##1) download
```
easyscrape download (url)
```
Function: Download the whole domain of the given url  
url: The absolute url of the domain

##2) scrape
```
easyscrape scrape (url) (data_extract_path)
```
Function: Crawl the given url and extract data to csv  
url: The absolute url of the domain  
data_extract_path: JSON file that contains an array of (colName, xPathString)  

###data_extract_path object format:
```json
[
	{
		"colName": "column name for csv",
		"xPathString": "xpath to the data you want to extract"
	},
	{
		"colName": "Column 1",
		"xPathString": "//div/text()"
	}
]
```
Basically, it will crawl the url given and extract any data that match the given xpath into the csv column  

##3) run
```
easyscrape run (settings)
```
Function: Run the given settings file, default settings is used if setting is not given  
\*Scroll to the bottom for settings file example.

###Default settings:
```json
{	
	"save_html_to_directory": false,
	"save_data_to_csv": false,
	"allowed_domains": [],
	"start_urls": [],
	"csv_output_file": "scrape_data.csv",
	"html_directory_name": "HTMLFiles",
	"save_file_regex": ".*",
	"remove_url_query": false,
	"deny_page_regex": [],
	"allow_page_regex": [],
	"randomize_download_delay": 0,
	"download_delay": 0,
	"depth_priority": 1,
	"data_extract_path": null
}
```

###1. save_html_to_directory | Value: boolean  
If True, download pages into the directory, If False, do nothing.  
Name of directory: (html_directory_name)  
Pages allowed: (allow_page_regex) - (deny_page_regex)  
Page naming: (save_file_regex)  

###2. save_data_to_csv | Value: boolean  
If True, extract data from pages that match the XPath and save them in CSV, If False, do nothing.  
Name of CSV output file: (csv_output_file)  
Pages allowed: (allow_page_regex) - (deny_page_regex)  
XPath to match: (data_extract_path)  

###3. allowed_domains | Value: array of strings  
An array of domains that the spider is allowed to crawl  
The spider will not visit domains that are not listed in (allowed_domains)  
Examples:  
```
["www.facebook.com"]  
["waynedev.me"]  
["quotes.toscrape.com", "www.google.com", "www.facebook.com"]  
```

###4. start_urls | Value: array of strings  
An array of absolute urls for the spider to start crawling  
The spider will start crawling from this list of urls  
Examples:
```
["https://www.facebook.com"]  
["http://quotes.toscrape.com", "https://www.wikipedia.org"]  
["https://docs.python.org/3/library/index.html"]  
```
