# 데이터 수집(웹 크롤링)
### News 헤드라인 가져오기


```python
from bs4 import BeautifulSoup
from urllib.request import urlopen
```


```python
# url 지정과 데이터 가져오기
url = 'https://news.naver.com/'
html_doc = urlopen(url)
soup = BeautifulSoup(html_doc,'html.parser')
```


```python
# mlist2 no_bg 내용 확인하기
soup
```


```python
soup.find_all('ul', 'mlist2 no_bg')
```


```python
soup.find_all('ul', 'mlist2 no_bg')[0]
```

### News 헤드라인 가져오기


```python
# 찾아낸 ul 블록들을 변수로 지정
blocks = soup.find_all('ul',{'class':'hdline_article_list'})
```


```python
# ul 블록들 안에 들어 있는 li들을 찾아 text, href 추출
hdline_list = []
for block in blocks:
    articles = block.find_all('li')
    for article in articles:
        title = article.find('a').text.strip()
        hdline_list.append(title)
        
hdline_list
```

### 정치, 경제, 사회, 생활/문화, 세계, IT/과학 등 기사

<div class="mtype_list_wide">
  <ul class="mlist2 no_bg>"
    <li>
      <a href=",,,
      </a>
         <i class="icon_photo">포토</i>
         <span class="writing">세계일보</span>
    </li>


```python
# 찾아낸 ul 블록들을 변수로 지정
blocks = soup.find_all('ul', 'mlist2 no_bg')
```


```python
# ul 블록들 안에 들어 있는 li들을 찾아 text, href 추출
article_list = []
for block in blocks:
    articles = block.find_all('li')
    for article in articles:
        title = article.find('a').text.strip()
        source = article.find('span').text.strip()
        link = article.find('a')['href']
        article_list.append([title,source,link])
        
article_list
```


```python

```
