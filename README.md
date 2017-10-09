
# Blog Crawler

* README:       https://github.com/Thecatdog/naver_blog_crawler
* Bug Reports:  https://github.com/Thecatdog/naver_blog_crawler/issues

## Description

Blog Crawler is an HTML parser for Naver Blog. It is based on Nokogiri and Mechanize.
Nokogiri's features is the ability to search documents via XPath or CSS3 selectors. 
Mechanize's feature is for following links and submit forms.

## System dependencies

* Nokogiri 1.8.1
* Mechanize 2.7

## Ruby version 

ruby 2.4.1

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


## Example

* crawler/noraml_blog.rb : for blog addressed "blog.naver.com"
* crawler/for_blog_me.rb : for blog addressed "blog.me"
* crawler/location_info.rb : it's scrapping location information like festival or fair.

## API Reference

* gem install nokogiri
* gem install mechanize

## Requirement

* require 'rubygems'
* require 'mechanize'
* require 'rest-client

__WARNING__

This is only for Naver Blog.
If you want to scrap another page, get page and form name.
Replace "sform" and "query" to what you get.

```ruby
	agent = Mechanize.new
	page = agent.get "http://naver.com"
	search_form = page.form_with :name => "sform"
	search_form.field_with(:name=>"query").value = key
```

## Development


## License


