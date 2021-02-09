```python
import requests
from bs4 import BeautifulSoup

LIMIT = 50
INDEED_URL=f"https://kr.indeed.com/jobs?q=python&limit={LIMIT}"

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

def extract_indeed_jobs(last_pages):
  jobs=[]
  #for page in range(last_pages):
  result = requests.get(f"{INDEED_URL}&start={0*LIMIT}")
  soup = BeautifulSoup(result.text, "html.parser")
  results=soup.find_all("div",{"class":"jobsearch-SerpJobCard"})
  for result in results:
    title=(result.find("h2", {"class": "title"}))
    title_anchor=title.find("a")["title"]

    company=result.find("span", {"class":"company"})
    company_anchor=company.find("a")

    if company_anchor is not None:
      company=(company_anchor.string)
    else:
      company=(company.string)

    company=company.strip()

    print(title_anchor, company)

  return jobs 

```


```python
max_indeed_pages=extract_indeed_pages()
extract_indeed_jobs(max_indeed_pages)
```

    데이터 분석가/사이언티스트(신입/인턴 가능) 쏘카
    2021년 2월 경력사원 세메스
    Data Scientist (KOREA) No Deviation Pte Ltd
    2021년 IITP 주관 글로벌핵심인재양성 지원사업 정보통신기획평가원
    Field Application YieldStar Competency Engineer ASML
    Application Engineer South Korea (Physics, EE) Zurich Instruments
    2021년도 한국알프스 수시 한국알프스
    SM파견 웹개발자 유저해빗
    프랭클린템플턴투신운용 Junior Trader (Quant base 필수) 프랭클린템플턴투신
    [빅데이터플랫폼] 데이터 엔지니어 한국카카오은행
    Sr Systems Administrator I Raytheon Intelligence & Space
    Application Engineer Consultant - HAV Mentor Graphics (Korea) LLC
    데이터 분석 및 컨설팅 분야 (Python, SAS, 빅데이터) 경력직 한국정보기술단
    [타다]데이터 분석가/사이언티스트 쏘카
    2021년 상반기 Python 경력 매크로액트
    Engr, Apps Dev 2 KLA-Tencor
    2021년 (신입) 전문연구요원 모집 NHN
    2021 Market Data Analyst - Seoul Bloomberg
    Engr, Tech Supp 3 KLA-Tencor
    지능형자동차부품진흥원 인력 지능형자동차부품진흥원
    2021 Global Data Internship - Seoul (Korean Speaker) Bloomberg
    Applied Data Scientist dunnhumby
    [전문연구요원] 상시 (전직) 네이버랩스
    [각 분야별] Java, MySQL, Python 외 정규직 로제타텍
    Developer / Designer recruit 마이뮤직테이스트
    Software Engineer - AI GE Appliances
    데이터 마케팅(분석/모델링) 전문가 LG전자
    각 부문별 수시 KIS채권평가
    Design Consultant, Staff Synopsys
    펌웨어, C·C++ 경력 계약직 아르비존
    [카카오커머스] 기술직군 카카오커머스
    스테코 부문별 신입 및 경력사원 스테코
    사물인터넷(IoT) 개발자 (하드웨어 및 소프트웨어) 큐빅스
    사내 및 서비스 보안 담당자 (경력) 네오위즈
    [전문연구요원] 빅데이터 엔지니어(신입/경력) 웹젠
    [4년제 대졸자 취업연계과정] 융합 SW 바이오 분야, 전공무관, 취업율 92.7 한국폴리텍대학분당융합기술교육원
    데이터 엔지니어(신입/경력) 쏘카
    글로벌 소셜카지노 서비스 해외사업 담당자 (경력) 네오위즈
    [EY한영] 금융감사본부 Data Analytics 전문 경력직 모집 Ernst & Young
    AI 분야 경력 LG CNS
    데이터 사이언스(데이터 모델링 및 추천 모델링) NHN
    Perception Software Engineer - Autonomous Vehicles NVIDIA
    [고경력자의 경우 시간단축] 홈페이지 개발 및 관리 웹프로그래머 규
    퀀트운용팀 (사원-대리급) 신한비엔피파리바자산운용
    Quantitative Researcher 자산운용: Quantitative Research
    에너지경제연구원 위촉연구원(에너지통계연구팀) 에너지경제연구원
    (광주취업맛집1위)2021년도 국비 기술교육생 대한상공회의소 광주인력개발원
    전문연구요원 (병역특례) 수시 (AI / HW 분야) 딥엑스
    글로벌 소셜카지노 부문 사업PM 네오위즈
    21년 전문연구요원 (AI엔지니어) Nexon
    




    []




```python

```
