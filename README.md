
 ```
 _   _                            _____                        _             
| \ | |                          /  __ \                      | |            
|  \| |  __ _ __   __ ___  _ __  | /  \/ _ __  __ _ __      __| |  ___  _ __ 
| . ` | / _` |\ \ / // _ \| '__| | |    | '__|/ _` |\ \ /\ / /| | / _ \| '__|
| |\  || (_| | \ V /|  __/| |    | \__/\| |  | (_| | \ V  V / | ||  __/| |   
\_| \_/ \__,_|  \_/  \___||_|     \____/|_|   \__,_|  \_/\_/  |_| \___||_|                                                 
 
 ```
* README:       https://github.com/Thecatdog/naver_crawler
* Bug Reports:  https://github.com/Thecatdog/naver_crawler/issues

## :star2: Description

Naver Crawler is an HTML parser for [Naver]("http://naver.com"). It is based on Nokogiri and Mechanize.
Nokogiri's features is the ability to search documents via XPath or CSS3 selectors. 
Mechanize's feature is for following links and submit forms.


## :pencil2: Features

- [x] Search with the naver search engine.
- [x] Link to the Blog pages.
- [x] Naver Blog Tags scrapping.
- [x] Scrapping Naver Calendar for festival and Fair.
- [ ] Naver Blog Main Contents scrapping.
- [ ] Extracting "Daum" and other various sites of blog posts.
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
	    
__PREFERENCE__

This is only for Naver Blog.
If you want to scrap another page, get page and form name.
Replace "sform" and "query" to what you get.

```ruby
	agent = Mechanize.new
	page = agent.get "http://naver.com"
	search_form = page.form_with :name => "sform"
	search_form.field_with(:name=>"query").value = key
```

ㅇㅂ

## Example

* crawler/noraml_blog.rb : for blog addressed "blog.naver.com"
* crawler/for_blog_me.rb : for blog addressed "blog.me"
* crawler/location_info.rb : it's scrapping location information like festival or fair.

## License
[GNU](https://github.com/Thecatdog/naver_crawler/blob/master/LICENSE)
