```python
pip install requests
```

    Requirement already satisfied: requests in c:\programdata\anaconda3\lib\site-packages (2.24.0)
    Requirement already satisfied: idna<3,>=2.5 in c:\programdata\anaconda3\lib\site-packages (from requests) (2.10)
    Requirement already satisfied: chardet<4,>=3.0.2 in c:\programdata\anaconda3\lib\site-packages (from requests) (3.0.4)
    Requirement already satisfied: urllib3!=1.25.0,!=1.25.1,<1.26,>=1.21.1 in c:\programdata\anaconda3\lib\site-packages (from requests) (1.25.11)
    Requirement already satisfied: certifi>=2017.4.17 in c:\programdata\anaconda3\lib\site-packages (from requests) (2020.6.20)
    Note: you may need to restart the kernel to use updated packages.
    


```python
pip install beautifulsoup4
```

    Requirement already satisfied: beautifulsoup4 in c:\programdata\anaconda3\lib\site-packages (4.9.3)
    Requirement already satisfied: soupsieve>1.2; python_version >= "3.0" in c:\programdata\anaconda3\lib\site-packages (from beautifulsoup4) (2.0.1)
    Note: you may need to restart the kernel to use updated packages.
    


```python
import requests
from bs4 import BeautifulSoup

INDEED_URL="https://kr.indeed.com/jobs?q=python&limit=50"

def extract_indeed_pages():
  result = requests.get(INDEED_URL)
  soup = BeautifulSoup(result.text, "html.parser")
  pagination=soup.find("div", {"class":"pagination"})
  
  pages=pagination.find_all('a')
  spans=[]
  for page in pages[:-1]:
     spans.append(int(page.string))
        
  max_page = spans[-1]

  return max_page
```


```python
max_indeed_pages=extract_indeed_pages()
print(max_indeed_pages)
```

    5
    

### 교훈1 주피터에서 빨간색은 무시해도 된다.
### 교훈2 from (indeed) import (extract_indeed_pages) <-- 한페이지에서 코드 검사할때는 불러올 필요 없음!!
