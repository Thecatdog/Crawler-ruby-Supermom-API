
 ```

███╗   ██╗ █████╗ ██╗   ██╗███████╗██████╗      ██████╗██████╗  █████╗ ██╗    ██╗██╗     ███████╗██████╗ 
████╗  ██║██╔══██╗██║   ██║██╔════╝██╔══██╗    ██╔════╝██╔══██╗██╔══██╗██║    ██║██║     ██╔════╝██╔══██╗
██╔██╗ ██║███████║██║   ██║█████╗  ██████╔╝    ██║     ██████╔╝███████║██║ █╗ ██║██║     █████╗  ██████╔╝
██║╚██╗██║██╔══██║╚██╗ ██╔╝██╔══╝  ██╔══██╗    ██║     ██╔══██╗██╔══██║██║███╗██║██║     ██╔══╝  ██╔══██╗
██║ ╚████║██║  ██║ ╚████╔╝ ███████╗██║  ██║    ╚██████╗██║  ██║██║  ██║╚███╔███╔╝███████╗███████╗██║  ██║
╚═╝  ╚═══╝╚═╝  ╚═╝  ╚═══╝  ╚══════╝╚═╝  ╚═╝     ╚═════╝╚═╝  ╚═╝╚═╝  ╚═╝ ╚══╝╚══╝ ╚══════╝╚══════╝╚═╝  ╚═╝
                                                                                                                  
 ```
 
* README:       https://github.com/Thecatdog/naver_crawler
* Bug Reports:  https://github.com/Thecatdog/naver_crawler/issues

## :star2: Description

네이버 크롤러는 [네이버]("http://naver.com")의 HTML 파일을 파싱합니다. 이 크롤러는 Nokogiri 와 Mechanize로 만들어졌습니다. 노코기리는 XPath나 CSS요소들을 이용해서 도큐먼트를 분석할 수 있습니다. 또한, Mechanize 같은 경우에는 link를 타고 들어가거나 submit같은 form에 변수를 입력해 결과물을 볼 수 있습니다.
Nokogiri 와 Mechanize 모두 HTML 파일을 파싱하는 크롤러지만, 각 크롤러가 가진 장점들을 이용하기 위해서 두 크롤러 모두를 사용했습니다.

## :pencil2: Features

- [x] 네이버 검색 엔진을 이용해서 데이터 검색.
- [x] '블로그'만 따로 모아 볼 수 있는 페이지로 이동.
- [x] 네이버 블로그 본문의 태그 저장.
- [ ] 네이버 블로그 본문 자체 저장.
- [ ] Daum을 포함한, 다른 여러 페이지 크롤링.
- [x] 네이버의 데이터 중 축제나 전시회의 날짜 정보 크롤링.
- [ ] Readability 기능 추가.


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
* keyword_rslt : Naver의 메인 페이지에서 검색 결과에 키워드를 넣어 결과를 보여주는 기능
parameter : 검색할 키워드
return value : Agent 객체

* shift_to_blog : 검색 결과 중 블로그만 따로 모아보기.
parameter : keyword_rslt 메소드의 결과의 Agent 객체 와 키워드.
return value : none   

* get_tag : 메인 블로그로 이동후, 블로그 내에 있는 태그들 뽑아오기.
parameter : 블로그 주소.
return value : array of tags

## HOW TO USE

```
./naver_crawler/crawler/Naver_crawler.rb 를 복사해서 본인의 프로젝트 디렉토리/lib에 넣으세요.

그 후 , 아래와 같은 코드를 본인이 사용할 controller에 작성하세요.
아래와 같은 코드를 이용해서 lib에 위치한 Naver_crawler의 클래스를 이용할 수 있습니다.

	require '~/workspace/lib/Naver_crawler.rb'
	naver = Naver_cralwer.new

```

## FILES

네이버 블로그의 주소 체계의 경우 세가지 경우의 수가 존재합니다.
상업적 주소를 제외한, blog.naver.com 과 blog.me 주소를 모두 크롤링 하기 위해서,
테스트를 위한 rb파일을 만들었습니다.

* crawler/noraml_blog.rb : "blog.naver.com"를 가진 주소를 크롤링.
* crawler/for_blog_me.rb : "blog.me"를 가진 주소를 크롤링.
* crawler/location_info.rb : 지역 축제나 전시회의 정보를 크롤링.

## Expanding

현재 Naver_crawler의 경우 Naver Blog 를 위주로 만들었습니다.
다른 페이지를 크롤링 하고 싶다면, form name query name을 알아내야 합니다.
"http://naver.com"에 원하는 주소를 입력합니다.
아래와 같은 코드에서 "sfrom"에 본인이 찾은 form name을 넣고, "query"에 본인이 찾은 query name을 넣으세요.
Mechanize의 agent객체가 본인이 입력한 페이지에 접근 할 것입니다.


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
	예를들어, DAUM 이라는 페이지를 크롤링 해봅니다.
	Daum 같은 경우에는 form name이 "daumSearch"이고, query name이 "q"입니다.

	agent = Mechanize.new
	page = agent.get "http://daum.net"
	search_form = page.form_with :name => "daumSearch"
	search_form.field_with(:name=>"q").value = key
	
	위와 같이 코드를 작성하시면 Daum 메인 페이지에 접근이 가능합니다.
	제대로 접근을 했는지 확인하기 위해서는 puts를 이용해서 link와 text를 출력해보세요.

```


## License

[GNU](https://github.com/Thecatdog/naver_crawler/blob/master/LICENSE)

