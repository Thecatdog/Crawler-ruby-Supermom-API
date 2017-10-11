
> ```
> _   _                            _____                        _             
>| \ | |                          /  __ \                      | |            
>|  \| |  __ _ __   __ ___  _ __  | /  \/ _ __  __ _ __      __| |  ___  _ __ 
>| . ` | / _` |\ \ / // _ \| '__| | |    | '__|/ _` |\ \ /\ / /| | / _ \| '__|
>| |\  || (_| | \ V /|  __/| |    | \__/\| |  | (_| | \ V  V / | ||  __/| |   
>\_| \_/ \__,_|  \_/  \___||_|     \____/|_|   \__,_|  \_/\_/  |_| \___||_|                                                 

* README:       https://github.com/Thecatdog/naver_blog_crawler
* Bug Reports:  https://github.com/Thecatdog/naver_blog_crawler/issues

## :star2: Description
Blog Crawler is an HTML parser for Naver Blog. It is based on Nokogiri and Mechanize.
Nokogiri's features is the ability to search documents via XPath or CSS3 selectors. 
Mechanize's feature is for following links and submit forms.

* The website receives information from the **user (mothers)**, as well as the input of the **child's** information.
* The server extracts the postings of the **Naver blog post based on the user's information**. The server outputs the most appropriate search results to the user's view.
* And The server removes the factors that let users worry about the results of the search. 
* The keywords that appear as a search result are calculated by using their own algorithm.
* The server then checks the frequency of the observed keyword and arranges it in descending order.
* Users can be provided **a better growth environment for their children** by using the information that the server has printed on the screen.

## :pencil2: Features

- [x] List of vaccination for user's child.
- [x] Measuring a child's growth.
- [x] Naver Blog scrapping and Information cleanup work.
- [x] Using ruby gem "twitter-korean-text" to Morphological analysis. 
- [ ] Extracting "Daum" and other various sites of blog posts.
- [ ] User-defiend preference category.
- [x] Show festivals and fairs at Calendar automatically.
- [ ] Extract website with readability that help us more than easy Morphological analysis.


## :computer: Overview


## User menual


## Ruby version 

ruby 2.4.1

## API Reference

* gem install nokogiri
* gem install mechanize


## Requirement

* require 'rubygems'
* require 'mechanize'
* require 'rest-client

## Development


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


## Example

* crawler/noraml_blog.rb : for blog addressed "blog.naver.com"
* crawler/for_blog_me.rb : for blog addressed "blog.me"
* crawler/location_info.rb : it's scrapping location information like festival or fair.

## License
[GNU](https://github.com/Thecatdog/naver_crawler/blob/master/LICENSE)
