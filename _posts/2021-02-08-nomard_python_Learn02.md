```python
pip install requests
```

    Requirement already satisfied: requests in c:\programdata\anaconda3\lib\site-packages (2.24.0)
    Requirement already satisfied: idna<3,>=2.5 in c:\programdata\anaconda3\lib\site-packages (from requests) (2.10)
    Requirement already satisfied: urllib3!=1.25.0,!=1.25.1,<1.26,>=1.21.1 in c:\programdata\anaconda3\lib\site-packages (from requests) (1.25.11)
    Requirement already satisfied: certifi>=2017.4.17 in c:\programdata\anaconda3\lib\site-packages (from requests) (2020.6.20)
    Requirement already satisfied: chardet<4,>=3.0.2 in c:\programdata\anaconda3\lib\site-packages (from requests) (3.0.4)
    Note: you may need to restart the kernel to use updated packages.
    


```python
pip install beautifulsoup4
```

    Requirement already satisfied: beautifulsoup4 in c:\programdata\anaconda3\lib\site-packages (4.9.3)
    Requirement already satisfied: soupsieve>1.2; python_version >= "3.0" in c:\programdata\anaconda3\lib\site-packages (from beautifulsoup4) (2.0.1)
    Note: you may need to restart the kernel to use updated packages.
    


```python
import requests
```


```python
from bs4 import BeautifulSoup
```


```python
indeed_result = requests.get("https://kr.indeed.com/jobs?q=python&limit=50")

print(indeed_result)
```

    <Response [200]>
    


```python
indeed_soup = BeautifulSoup(indeed_result.text, 'html.parser')
```


```python
pagination=indeed_soup.find("div", {"class":"pagination"})
print(pagination)
```

    <div class="pagination" onmousedown="pclk(event);">
    <ul class="pagination-list"><li><b aria-current="true" aria-label="1" tabindex="0">1</b></li><li><a aria-label="2" data-pp="gQAyAAAAAAAAAAAAAAABmixKkwBjAQEBCgHBShmmSrqMUH1bJSdcq9sr7TioFX0Qu_laGerDLfUjITHMi0FndpxFTSlv49sxCJLjzZQqM-bQk_34mEtcoTbHGKzlrAdoGY3vHVDxvPgf6uyRtU7g5DX6A04UT8uWAAA" href="/jobs?q=python&amp;limit=50&amp;start=50" onmousedown="addPPUrlParam &amp;&amp; addPPUrlParam(this);" rel="nofollow"><span class="pn">2</span></a></li><li><a aria-label="3" data-pp="gQBkAAAAAAAAAAAAAAABmixKkwCaAQMBHUALcgcFEAeeM0Vi6Ryy4l4TnbeopCtqE6R8IMsxomcAt_yNsx4PSpfPVmyu9hQTKbZtjEyBxpnEm36ZAxjxSGRJGna8L20UgSqR7is4nKCNtXAdxGVWSmKd7fhYkE_G3dsG4eJm5ITl9KCa-bUTsKo3Niwgq2efvo5ifVYuzCAUWp03UH-MMQR44aNnVXZpZjBabRUIfwAA" href="/jobs?q=python&amp;limit=50&amp;start=100" onmousedown="addPPUrlParam &amp;&amp; addPPUrlParam(this);" rel="nofollow"><span class="pn">3</span></a></li><li><a aria-label="4" data-pp="gQCWAAAAAAAAAAAAAAABmixKkwC9AQQBH0ALMAdICQXgPe81Y0IsTgz7qy1w_XBvkd24--Gp_Yx7PuCDEahhp1IYn2pUf36zROlbHGn0OKbC5GnazewppcESGMsZGdi-wFRnYpk3jpeRNFAVgpCm9Hlf2WMLGNDF2lYvnsBPfgTKcQfvRbbmHzLMuZUuVxt-cF4apSVGJulsbguKudBHlktXusm0-kC_tzkCfFkMcNw3hIwhHkForUgqe84re4Z7pulnYX9FewJsqUGYceRn8aLsAAA" href="/jobs?q=python&amp;limit=50&amp;start=150" onmousedown="addPPUrlParam &amp;&amp; addPPUrlParam(this);" rel="nofollow"><span class="pn">4</span></a></li><li><a aria-label="5" data-pp="gQDIAAAAAAAAAAAAAAABmixKkwDUAQMBP4IBCDwJEw-1_VxmBT3tqqUAqlSn8JFrDGpNEPT1mVltxKTX2wAPfJOwdFuAGRrVYOnxxgSCaeaK3_Zvz9c5iGclBzsdyjigQ2iDHkZGLXBDi1zokTq93Le0vZV4nlWu_LVqHLhh2TmU32R1rpfhWrVbTSwTrLKd6gB2qtzCJ_LR_BairHF_UMnQ4hEeenLINRdlzyp8TcB7uKs0A-OoCsa4qnkeshXaUkzDJQvR5-IgW5jGcPG4YgzNUFk4v1Dy8wmkvUxA0vlz5-MTERTBH9AAAA" href="/jobs?q=python&amp;limit=50&amp;start=200" onmousedown="addPPUrlParam &amp;&amp; addPPUrlParam(this);" rel="nofollow"><span class="pn">5</span></a></li><li><a aria-label="다음" data-pp="gQAyAAAAAAAAAAAAAAABmixKkwBjAQEBCgHBShmmSrqMUH1bJSdcq9sr7TioFX0Qu_laGerDLfUjITHMi0FndpxFTSlv49sxCJLjzZQqM-bQk_34mEtcoTbHGKzlrAdoGY3vHVDxvPgf6uyRtU7g5DX6A04UT8uWAAA" href="/jobs?q=python&amp;limit=50&amp;start=50" onmousedown="addPPUrlParam &amp;&amp; addPPUrlParam(this);" rel="nofollow"><span class="pn"><span class="np"><svg fill="none" height="24" width="24"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6-6-6z" fill="#2D2D2D"></path></svg></span></span></a></li></ul></div>
    


```python
pages=pagination.find_all('a')
```


```python
spans=[]
for page in pages[:-1]:
    spans.append(int(page.string))
    
max_page = spans[-1]

print(max_page)
```

    5
    


```python
print(range(max_page))
```

    range(0, 5)
    


```python

```
