[![Build Status](https://travis-ci.org/Thecatdog/Naver_Crawler-ruby-Supermom-API.png?branch=master)](https://travis-ci.org/Thecatdog/Naver_Crawler-ruby-Supermom-API)
 ```

███╗   ██╗ █████╗ ██╗   ██╗███████╗██████╗      ██████╗██████╗  █████╗ ██╗    ██╗██╗     ███████╗██████╗ 
████╗  ██║██╔══██╗██║   ██║██╔════╝██╔══██╗    ██╔════╝██╔══██╗██╔══██╗██║    ██║██║     ██╔════╝██╔══██╗
██╔██╗ ██║███████║██║   ██║█████╗  ██████╔╝    ██║     ██████╔╝███████║██║ █╗ ██║██║     █████╗  ██████╔╝
██║╚██╗██║██╔══██║╚██╗ ██╔╝██╔══╝  ██╔══██╗    ██║     ██╔══██╗██╔══██║██║███╗██║██║     ██╔══╝  ██╔══██╗
██║ ╚████║██║  ██║ ╚████╔╝ ███████╗██║  ██║    ╚██████╗██║  ██║██║  ██║╚███╔███╔╝███████╗███████╗██║  ██║
╚═╝  ╚═══╝╚═╝  ╚═╝  ╚═══╝  ╚══════╝╚═╝  ╚═╝     ╚═════╝╚═╝  ╚═╝╚═╝  ╚═╝ ╚══╝╚══╝ ╚══════╝╚══════╝╚═╝  ╚═╝
                                                                                                                  
 ```
 

 
* README:       https://github.com/Thecatdog/Naver_Crawler-ruby-Supermom-API
* Bug Reports:  https://github.com/Thecatdog/Naver_Crawler-ruby-Supermom-API/issues

## :star2: Description

Naver Crawler is an HTML parser for [Naver]("http://naver.com"). It is based on Nokogiri and Mechanize.
Nokogiri's features is the ability to search documents via XPath or CSS3 selectors. 
Mechanize's feature is for following links and submit forms.


## :pencil2: Features

- [x] Search with the naver search engine.
- [x] Link to the Blog pages.
- [x] Naver Blog Tags scrapping.
- [ ] Naver Blog Main Contents scrapping.
- [ ] Extracting "Daum" and other various sites of blog posts.
- [x] Scrapping Naver Calendar for festival and Fair.
- [ ] Extract website with readability.


## Ruby version 

ruby 2.4.1

## API Reference

* gem install nokogiri
* gem install mechanize

## Requirement

* require 'rubygems'
* require 'mechanize'
* require 'rest-client

## Methods
 
* keyword_rslt : get result from searching keyword on Naver main page.
		 parameter : keyword to search,
		 return value : agent object
                
* shift_to_blog : link to blog page from result page.
                  parameter : the return object from keyword_rslt method, keyword for search,
                  return value : none        
                  
* get_tag : get tags from blog content.
            parameter : blog link uri,
            return value : array of tags

## HOW TO USE

```
cp ./naver_crawler/crawler/Naver_crawler.rb [your project dir]/lib/

And put below codes at your Controller.

	require '~/workspace/lib/Naver_crawler.rb'
	naver = Naver_cralwer.new

Then you can use Naver_crawler Class and Methods.


```

## FILES

* crawler/noraml_blog.rb : for blog addressed "blog.naver.com"
* crawler/for_blog_me.rb : for blog addressed "blog.me"
* crawler/location_info.rb : it's scrapping location information like festival or fair.


## Expanding

This is only for Naver Blog.
If you want to scrap another page, get page and form name.
Replace "sform" and "query" to what you get.

./naver_crawler/crawler/Naver_crawler.rb
```
   
	agent = Mechanize.new
	page = agent.get "http://naver.com"
	search_form = page.form_with :name => "sform"
	search_form.field_with(:name=>"query").value = key
   
```

_EXAMPLE_
* www.daum.net

```
	Replace "sform" to "daumSearch" and "query" to "q".
	
	agent = Mechanize.new
	page = agent.get "http://daum.net"
	search_form = page.form_with :name => "daumSearch"
	search_form.field_with(:name=>"q").value = key
	
	Then You can access to Daum.
	For test, Try "puts page.link" and "puts page.text".

```


## License

[GNU](https://github.com/Thecatdog/Naver_Crawler-ruby-Supermom-API/blob/master/LICENSE)

