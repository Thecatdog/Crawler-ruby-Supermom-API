
# Naver Blog Crawler

* README:       https://github.com/Thecatdog/naver_blog_crawler
* Bug Reports:  https://github.com/Thecatdog/naver_blog_crawler/issues

## Description

Naver Blog Crawler is an HTML parser for Naver Blog. It is based on Nokogiri and Mechanize.
Nokogiri's features is the ability to search documents via XPath or CSS3 selectors. and Mechanize's feature is for following links and submit forms.

## System dependencies

* Nokogiri 1.8.1
* Mechanize 2.7

## Ruby version 

ruby 2.4.1

## Methods
 
* keyword_rslt : 네이버 본문에서 keyword 검색 결과 가져오기
                 parameter : keyword to search
                 return value : agent object
                
* shift_to_blog : 메인에서 블로그만 모아 보기
                  parameter : the return object from keyword_rslt method, keyword for search
                  return value : none        
                  
* get_tag : BLOG 본문에 들어가 tag들을 가져오는 메소드 
            parameter : blog link uri
            return value : array of tags


## Features

* crawler/noraml_blog.rb : for blog addressed "blog.naver.com"
* crawler/for_blog_me.rb : for blog addressed "blog.me"
* crawler/location_info.rb : it's scrapping location information like festival or fair.

## Installation

* gem install nokogiri
* gem install mechanize

## Requirement
* require 'rubygems'
*	require 'mechanize'
*	require 'rest-client


__WARNING__

Some documents declare one encoding, but actually use a different
one. In these cases, which encoding should the parser choose?

Data is just a stream of bytes. Humans add meaning to that stream. Any
particular set of bytes could be valid characters in multiple
encodings, so detecting encoding with 100% accuracy is not
possible. `libxml2` does its best, but it can't be right all the time.

If you want Nokogiri to handle the document encoding properly, your
best bet is to explicitly set the encoding.  Here is an example of
explicitly setting the encoding to EUC-JP on the parser:

```ruby
  agent = Mechanize.new
		page = agent.get "http://naver.com"
		search_form = page.form_with :name => "sform"
		search_form.field_with(:name=>"query").value = key
```

## Development


## License


