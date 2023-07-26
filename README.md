# AIS8_Final_Project
<p align="center"><img src="https://user-images.githubusercontent.com/125840482/236968175-4dcfc8c9-5135-40d0-82ec-19b137496b85.jpg" width="800" height="400"/></p>

# **1-1. 주제**
## 📌 **HR Data를 활용한 퇴사 예측 모델 구현**
Kaggle의 ‘****IBM HR Analytics Employee Attrition & Performance****’ 데이터를 활용해 퇴사 여부에 영향을 미치는 HR Data를 분석한다. 분석 결과를 통해 인사담당자들에게 인재 유출을 방지하기 위한 지표 개선의 근거를 제공하고자 한다.
<br/><br/>

# **1-2. 주제 선정의 배경**

## 💡 이직을 RESPECT, MZ를 중심으로 대퇴사 시대
<p align="center"><img src="https://user-images.githubusercontent.com/125840482/236966761-134dda8d-4c69-4327-92ae-68331caef7fd.png" width="600" height="350"/></p>
<p align="center">이미지 출처 : 잡코리아</p>

22년 말, 구인구직 플랫폼 ‘잡코리아’는 ‘**이직을 RESPECT**’한다는 광고를 선보였다. 이는 구인구직 플랫폼의 주 타겟층이 취준생에서 이직(퇴사)을 준비하는 직장인으로 확대되었다는 것을 의미한다. ‘평생직장’이라는 말이 구시대적으로 느껴지는 지금, 이 광고를 통해 우리는 **이직, 퇴사가 첫 직장을 구하는 것만큼 빈번하게 일어나고 있는 시대상**을 볼 수 있다.<br/><br/>

![image](https://user-images.githubusercontent.com/125840482/236966835-0227b626-fdff-41fe-aa5e-5ed77090e5b5.png)
출처 : [https://www.asiae.co.kr/article/2022072616513391421](https://www.asiae.co.kr/article/2022072616513391421)

 통계청에 따르면 22년 5월 기준 **청년층의 첫 직장 평균 근속기간은 1년6.8개월**이다. 첫 직장으로 임금근로 일자리를 얻은 **15~29세 청년층의 65.6%는 졸업 후 가진 첫 일자리를 그만뒀다**. 취업플랫폼 사람인이 21년 500개 기업을 대상으로 '1년 이내 조기퇴사자' 현황에 대해 조사한 결과, **응답 기업의 49.2%는 'MZ세대의 조기퇴사율이 높다'**고 답했다. 20·30세대들이 퇴사를 결심하는 이유로는 '더 좋은 회사로의 이직 준비'(20대 56.3%, 30대 55.7%)가 가장 많았다.**<br/><br/> 

## 💡 직원 1명 당 채용비용 1300만원, 교육비용 6000만원

|<img src="https://user-images.githubusercontent.com/125840482/236966871-3efbea42-d2e4-4e9e-8bcf-7fc540875d59.png" width="400" height="300">|<img src="https://user-images.githubusercontent.com/125840482/236967053-c86774b3-bc0e-44ae-a493-57e7209d833c.png" width="800" height="300">|
|:----:|:------:|
|이미지 출처 : [https://www.saramin.co.kr/zf_user/help/live/view?idx=108748&listType=news](https://www.saramin.co.kr/zf_user/help/live/view?idx=108748&listType=news)|이미지 출처 : [https://post.naver.com/viewer/postView.nhn?memberNo=24090434&volumeNo=6470527](https://post.naver.com/viewer/postView.nhn?memberNo=24090434&volumeNo=6470527)|<br/><br/>

 이러한 상황은 기업 인적자원(HR) 담당자 입장에서 큰 고민거리이다. 조기퇴사자의 증가로 인한 다양한 손해가 있지만 금전적 손실이 특히 크다. 커리어테크 플랫폼 사람인이 기업 499개사를 대상으로 ‘직원 채용 시간과 비용’에 대해 조사한 결과, **직원 1인 채용에 평균 32일, 1,272만원의 비용**이 드는 것으로 조사됐다. 또한, 한국경영자총협회가 2013년 발표한 **대졸 신입사원 1인당 교육 비용은 평균 5960만원**이다. 최문석 한국경영자총연합회 경제조사2팀장은 “교육비용에는 신입사원이 업무 역량을 본격 발휘할 때까지 지급된 월급도 포함된다”며 “조기 퇴사가 늘어나면 기업의 손실도 그만큼 증가할 수밖에 없다”고 말했다.
<br/><br/>


## 💡 HR Analytics : HR 문제, 데이터로 해결하다
![image](https://user-images.githubusercontent.com/125840482/236967350-cb0114a4-69fb-4e8c-b6eb-79ac1d002afa.png)
이미지 출처 : [https://www.servicenow.com/kr/products/hr-service-delivery/what-is-hr-analytics.html](https://www.servicenow.com/kr/products/hr-service-delivery/what-is-hr-analytics.html)

우리는 퇴사율을 줄이고 리텐션을 높이는 방법, 퇴사의 진짜 원인을 찾고 개선점을 마련하기 위한 방법으로 HR Analytics를 선택했다. **HR Analytics**란 **다양한 방법론과 도구를 활용하여 인적자원 데이터를 분석하고, 사업과 조직의 성과를 향상시키는 의사결정을 지원하는 활동**이다. HR관련 업무는 주로 주관적인 성과 평가 및 민감한 개인정보를 다루기 때문에 데이터를 활용하는 것에 제약이 많았다. 하지만 HR 분야에서의 데이터 기반 의사결정이 직무 만족도 향상, 조직문화 개선, 퇴사율 감소 등 성과를 내기 시작하면서 많은 기업에서 HR Analytics를 도입하고 있다. HR Analytics를 활용한 우수 사례들은 다음과 같다.
<br/><br/>

|**HR Analytics 사용사례**|  |
|:---------|------------|
|<img src="https://user-images.githubusercontent.com/125840482/236967322-e2f528b6-aac9-47bb-9d8a-c1d3b9ac5061.png" width="400" height="400"> <br> 이미지 출처 : [https://www.etoday.co.kr/news/view/1747355](https://www.etoday.co.kr/news/view/1747355)| 1. **퇴사 예측 인공지능** <br> IBM은 퇴사할 직원을 95% 정확도로 예측할 수 있는 인공지능을 개발했다. ‘선제적 소모 프로그램(Predictive Attrition Program)‘으로 불리는 이 기술은 퇴사 리스크가 있는 직원을 AI가 추려내 관리자들이 대체 인력을 선제적으로 고용할 수 있도록 하는 프로그램이다. 이 기술로 IBM은 지금까지 약 3억 달러(약 3400억 원)의 비용을 절감했다.|
| 2. **HR 시각화 대시보드** <br> 다양한 HR 데이터를 대시보드로 제작해 전 직원을 효율적으로 관리할 수 있다. 이는 실무진이 실시간 HR 데이터를 살펴보며 개인, 조직, 회사의 개선 사항이 무엇인지 단계별로 찾을 수 있도록 도와준다. 이를 테면, 퇴사율이 높은 직무를 중심으로 퇴사 원인을 탐색하여 일괄적인 해결방안(ex. 연봉상승) 대신 구체적인 조치를 취할 수 있다. | <img src="https://user-images.githubusercontent.com/125840482/236967300-22b7ad7f-bbac-4ad8-ae00-7dfa02372265.png" width="400" height="200"> <br> 이미지 출처 : [https://www.simplesheets.co/hr-metrics-dashboard](https://www.simplesheets.co/hr-metrics-dashboard)|
<br/><br/><br/>

# **1-3. 프로젝트 목표**

 본 프로젝트는 Kaggle의 ‘IBM HR Analytics Employee Attrition & Performance’ 데이터를 바탕으로 퇴사에 가장 큰 영향을 미치는 변수를 찾고자한다. 따라서 HR data를 활용해 직원의 퇴사 여부를 예측하는 머신러닝 모델을 구축하고 퇴사 현황과 원인을 파악할 수 있는 대시보드를 제작하여 HR 부서의 인력 계획 의사결정의 인사이트를 제공하는 것이 목표이다. 

1. 탐색적 데이터 분석(EDA)을 통해 퇴사 여부 예측 머신러닝 모델 구축
2. 퇴사 원인을 탐색적으로 파악할 수 있는 시각화 대시보드 제작

# **1-4. 프로젝트 결과물**
* 결과 정리 노션
   [결과물 노션](https://seyeoncho.notion.site/Final-59cb66bfb858491691d3b2932bb717e9?pvs=4)
* 결과보고 ppt
* [시각화 대시보드](https://public.tableau.com/app/profile/seyeon.cho/viz/Final_HR_Analytics_0505/DashBoard)
    ![image](https://user-images.githubusercontent.com/125840482/236977299-4fac6006-2f9f-4026-8a7e-5477730f51c6.png)
* HR 데이터 수집 설문 예시
   * **설문조사 응답자용(임직원)**
   [[HR]임직원 의견 수렴 조사(설문 응답용)](https://forms.gle/ma7nRXcB7aDQbZCx6)

   * **설문조사 취합용(HR팀)**
   [[HR]임직원 의견 수렴 조사(HR팀 확인용)](https://forms.gle/U4KLKZiQv3tYEE4D6)
