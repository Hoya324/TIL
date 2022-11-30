2022.11.22(일)

# 스프링 웹 개발 기초

### 정적 컨텐츠
 그냥 파일을 내려줌

### MVC와 템플릿 엔진
 템플릿 엔진을 model, view, controller 방식으로 쪼개서 뷰를 템플릿 엔진으로 html으로 랜더링해서 랜더링이 된 html을 고객에게 전달

### API
객체를 반환하는 것(Hello hello = new Hello();에서 hello)
-> HttpMessageConverter로 json 포맷으로 전달.
@ResponseBody를 사용

# 회원 관리 예제

### 비즈니스 요구사항 정리
- 데이터: 회원ID,이름
- 기능: 회원 등록, 조회
- 아직 데이터 저장소가 선정되지 않음(가상의 시나리오) 
<img width="369" alt="스크린샷 2022-11-20 오후 5 42 41" src="https://user-images.githubusercontent.com/96857599/202893212-1a6e420d-f81e-4872-9906-3dcbc4ee2582.png">

<img width="384" alt="스크린샷 2022-11-20 오후 5 50 48" src="https://user-images.githubusercontent.com/96857599/202893496-a70bb101-7789-4a55-a20d-d1ada18fdd4b.png">

### 테스크 케이스 작성
<img width="314" alt="스크린샷 2022-11-30 오후 2 49 31" src="https://user-images.githubusercontent.com/96857599/204717914-75b3dcfa-c2d7-4d02-a8d7-466db2d987bd.png">

te
