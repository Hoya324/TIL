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

### 테스트 케이스 작성
<img width="314" alt="스크린샷 2022-11-30 오후 2 49 31" src="https://user-images.githubusercontent.com/96857599/204717914-75b3dcfa-c2d7-4d02-a8d7-466db2d987bd.png">

1. test > hello.hellospring 폴더에 repository 폴더 생성(테스트하고자 하는 폴더라 같은 이름
2. MemoryMemberRepository 클래스를 테스트할 것이므로 MemoryMemberRepositoryTest 클래스 생성
<img width="508" alt="스크린샷 2022-11-30 오후 2 53 27" src="https://user-images.githubusercontent.com/96857599/204718465-7cc7ffc1-0c48-4175-86db-60f603d761b9.png">
3. @Test를 작성하므로써 설계한 내용이 잘 작동하는지 확인하도록한다.

4. save 메서드 Test 작성
<img width="509" alt="스크린샷 2022-11-30 오후 2 57 10" src="https://user-images.githubusercontent.com/96857599/204718992-49b1dfdd-8105-4836-bd5e-bf128e264c13.png">
5. 확인방법 3가지

5-1. 같은지 확인하고 True/False 출력
<img width="335" alt="스크린샷 2022-11-30 오후 3 03 15" src="https://user-images.githubusercontent.com/96857599/204720611-38c431b8-7ffe-4e6e-862a-89a086cd73c4.png">

5-2. Assertions junit jupiter api
<img width="557" alt="스크린샷 2022-11-30 오후 3 07 31" src="https://user-images.githubusercontent.com/96857599/204720952-463d39a3-147a-44b4-a38e-7646c5443745.png">
<img width="332" alt="스크린샷 2022-11-30 오후 3 11 00" src="https://user-images.githubusercontent.com/96857599/204721007-d1a96bd0-b3b6-4b34-af0c-0f3294f41d3f.png">

5-3. Assertions assertj core api (많이 씀)
<img width="335" alt="스크린샷 2022-11-30 오후 3 03 15" src="https://user-images.githubusercontent.com/96857599/204721167-7a1b08c6-d075-418e-be1e-26b51ee0953f.png">
<img width="398" alt="스크린샷 2022-11-30 오후 3 13 04" src="https://user-images.githubusercontent.com/96857599/204721352-ff5e8db2-e6fc-489e-9f51-7296193c2d87.png">

TIP! 이때, option + enter 키를 누르면
<img width="466" alt="스크린샷 2022-11-30 오후 3 04 43" src="https://user-images.githubusercontent.com/96857599/204721590-2e48aef9-4be4-422a-9cfd-adf8f7a1a81d.png">
static 클래스로 사용가능하다.

6. 같은 방법으로 findByName()과 findAll() 테스트 코드를 작성한다.
<img width="494" alt="스크린샷 2022-11-30 오후 3 37 21" src="https://user-images.githubusercontent.com/96857599/204725142-bda02d97-273c-4c37-8aec-655dd5717c6b.png">
<img width="427" alt="스크린샷 2022-11-30 오후 3 37 34" src="https://user-images.githubusercontent.com/96857599/204725187-11e30c17-d0be-43f1-b9c9-fccaa79274c5.png">

TIP! 같은 내용의 인스턴스 이름만 다르다며 shift + F6키로 rename이 가능하다.

7. 이 상태로 테스트를 진행하며 repository에 이미 저장된 데이터가 중복되 수 있으므로, main 폴더의 MemoryMemberRepository 클래스에 데이터를 초기화시켜주는 메소드를 작성하고 Test에서 하나의 테스트가 끝나면 저장소 등 공용 데이터를 모두 지워주는 메서드를 작성한다.
- @AfterEach를 작성하지 않았을 때
<img width="208" alt="스크린샷 2022-11-30 오후 3 28 06" src="https://user-images.githubusercontent.com/96857599/204726011-edc42da5-e192-44e6-a790-c89fda258852.png">
- 작성
<img width="236" alt="스크린샷 2022-11-30 오후 3 30 47" src="https://user-images.githubusercontent.com/96857599/204726053-acf8c963-4f95-422b-b744-c9ae4be8f497.png">
<img width="249" alt="스크린샷 2022-11-30 오후 3 31 34" src="https://user-images.githubusercontent.com/96857599/204726070-25c57fbf-fc62-4399-925d-db44fee34cb1.png">
- 작성 후
<img width="196" alt="스크린샷 2022-11-30 오후 3 43 08" src="https://user-images.githubusercontent.com/96857599/204726137-8f31f3c8-4dac-428f-b401-ce51a8c9059d.png">


5-3. Assertions assertj core api (많이 씀)ㅇ
5-3. Assertions assertj core api (많이 
