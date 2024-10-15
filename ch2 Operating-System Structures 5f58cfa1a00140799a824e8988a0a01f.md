# ch2 Operating-System Structures

생성일: 2023년 10월 10일 오후 7:52

# CHAPTER 2 - 시스템 구조 (System Structures)

## **운영체제 서비스(Operating System Service)**

![Untitled](ch2%20Operating-System%20Structures%205f58cfa1a00140799a824e8988a0a01f/Untitled.png)

**사용자 인터페이스(User interface)**  

1-(1) CLI(Command Line Interface) : 문자열로 명령하는 인터페이스를 제공함.  

1-(2) Batch Interace : 디렉티브가 파일 형태로 입력되고, 파일을 통해 인터페이스를 제공함.  

1-(3) GUI(Graphical User Interface) : 가장 보편적. 그래픽 요소들을 통해 인터페이스를 제공함.

**프로그램 수행(Program Execution)**

**입출력 연산(I/O Operation)**

**파일 시스템 조작(File System Manipulation)**

**통신(Communication)**

**오류 탐지(Error Detection)**

**자원 할당(Resource Allocation)**

**로깅(Logging) - 얼마나 어떤 종류의 자원을 프로그램을 작업하는 동안 사용했는지 추적**

**보호(Protection)와 보안(Security)**

## **시스템 호출(System Calls)**

`System Call`은 OS에 의해 사용 가능하게 된 서비스에 대한 인터페이스를 제공한다.

- 대부분, 프로그래머들은 API(Application Programming Interface)를 통해 System Call을 호출한다.
- API 사용자는 System Call이 어떻게 구현되고, 실행 중 무슨 작업을 하는지 알지 못해도 되며, 단지 API를 준수하고, 시스템 호출의 결과로서 운영체제가 무엇을 할 것인지 만을 파악하면 된다.
- `런타임 환경(RTE)`은 시스템 호출 인터페이스를 제공한다. 시스템 호출 인터페이스를 제공한다.
    
    ![스크린샷 2023-10-10 오후 8.05.30.png](ch2%20Operating-System%20Structures%205f58cfa1a00140799a824e8988a0a01f/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-10_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_8.05.30.png)
    
- 운영체제에 매개변수를 전달하는 방법은 크게 3가지가 있다.

1. 매개변수를 레지스터 내에 전달하는 방법

2. 매개변수를 메모리 내의 블록이나 테이블에 저장하고, 블록의 주소가 레지스터 내에 저장되는 방법

![스크린샷 2023-10-10 오후 8.07.47.png](ch2%20Operating-System%20Structures%205f58cfa1a00140799a824e8988a0a01f/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-10_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_8.07.47.png)

3. 매개변수를 블록이나 스택에 저장하는 방법 (매개변수의 길이를 제한하지 않는 장점이 있음.)

## **시스템 호출의 유형 (Types of System Calls)**

1. Process Control (프로세스 제어)

2. File Manipulation (파일 조작)

3. Device Manipulation (장치 조작)

4. Information Maintance (정보 유지 보수)

5. Communication (통신)과 Protection (보호)

## **시스템 프로그램(System Programs)**

시스템 프로그램은 시스템 유틸리티(System Utility)로 알려져 있으며, 프로그램 개발과 실행을 위해보다 편리한 환경을 제공한다.

시스템 프로그램(System Program)은 **파일 관리, 상태 정보, 파일 변경, 프로그래밍 언어 지원, 프로그램 적재와 수행, 통신, 백그라운드 서비스**의 범주로 분류할 수 있다.

## Linkers and Loaders

![Untitled](ch2%20Operating-System%20Structures%205f58cfa1a00140799a824e8988a0a01f/Untitled%201.png)

![Untitled](ch2%20Operating-System%20Structures%205f58cfa1a00140799a824e8988a0a01f/Untitled%202.png)

- Source files are compiled into object files designed to be loaded into
any physical memory location, know as `relocatable object files`
- `Linker` combines relocatable object files into a single binary
executable file. Other object files or libraries may be included.
- `링커` : 재배치 가능 오브젝트 파일을 하나의 **이진 실행 파일**로 결합
    - 링킹 단계에서 다른 오브젝트 파일 또는 라이브러리 포함될 수 있음
        - 표준 C 라이브러리, 수학 라이브러리 등
- `Loader` loads binary executable file into memory to run on a CPU
core.
- `로더` : 이진 실행 파일을 메모리에 적재
    - 프로그램 부분에 최종 주소를 할당, 프로그램 코드와 데이터를 해당 주소와 일치하도록 조정
    - 프로그램이 실행될 때, 코드가 라이브러리 함수를 호출하고 변수에 접근할 수 있도록 함
    - 실제 대부분의 시스템은 프로그램을 적재할 때 라이브러리를 동적으로 링크
        - Windows는 **동적 링킹 라이브러리(DLL)를** 지원
- `Relocation`(linking + loading) assigns final addresses to program
parts and adjusts code and data in program to match those
addresses

### Why Applications are OS Specific

- 한 OS에서 컴파일된 응용 프로그램은 다른 운영 체제에서 실행할 수 없습니다.
- An application designed to call one set of APIs(e.g. available from iOS)
will not work on an OS that does not provide those APIs ( such as
Android)
- CPU에는 다양한 명령어 세트가 있으며, 적절한 명령어가 포함된 애플리케이션만 명령어를 포함하는 애플리케이션만 올바르게 실행할 수 있습니다.
    - CPUs have varying instruction sets, and only applications containing the appropriate instructions can execute correctly.
- System calls vary among OS in many respects, including

## **운영체제 구조 (Operating-System Structures)**

### Monolithic Structure

- 구조가 없는 가장 단순한 구조로 OS를 구성할 수 있습니다.
- 커널의 모든 기능은 단일 주소 공간에서 실행되는 단일 정적 바이너리 단일 주소 공간에서 실행되는 단일 정적 바이너리 파일에 배치됩니다.
- 단점: 확장 어려움
- 장점: 뚜렷한 성능 이점(속도 및 효율성)
    - 시스템 호출 인터페이스의 오버헤드가 거의 없음
    - 커널 내 통신이 빠릅니다.

**Traditional UNIX System structure.**

![Untitled](ch2%20Operating-System%20Structures%205f58cfa1a00140799a824e8988a0a01f/Untitled%203.png)

### Layered Approach

- 적절한 hardware support가 있을 경우, 운영체제는 보다 적절하게 분할될 수 있다.
- 운영체제가 여러 층으로 나누어진다.
- 최하위 층(Layer 0)는 Hardware이고, 최상위 층(Layer N)은 User Interface이다.
- 계층적 구조에서, 특정 층 M은 자료구조와 상위 층에서 호출할 수 있는 루틴의 집합으로 구성된다.
- 모듈화를 통해 레이어는 각각 하위 레이어의 기능(작업) 및 서비스만 사용하도록 선택됩니다.
- 장점: 한 구성 요소의 변경 사항은 해당 구성 요소에만 영향을 미칩니다.
    
           :구성의 단순성 및 디버깅
    
- 단점: 전반적인 성능이 좋지 않습니다. 사용자 프로그램이 사용자 프로그램이 여러 레이어를 여러 계층을 통과해야 하는 오버헤드 때문에 전반적인 성능이 떨어집니다.

### Microkernels

- 중요치 않은 구성 요소들을 커널로부터 제거하고, 그것들을 System 및 User level Program으로 구현하여 운영체제를 구성하는 방법이다.

![Untitled](ch2%20Operating-System%20Structures%205f58cfa1a00140799a824e8988a0a01f/Untitled%204.png)

- 마이크로 커널의 주 기능은 **Client Program과 User Space에서 수행되는 다양한 서비스 간에 Communication을 제공하는 것이다.** (통신은 **Message Passing**을 통해 제공된다.)
- 장점: 운영체제의 확장에 용이하다
    
           : 모든 새로운 서비스는 사용자 공간에 추가되므로, Kernel의 변경을 필요로 하지 않는다.
    
     :불가피하게 커널이 변경되어야 할 때에도, 비교적 커널의 크기가 작아 변경할 대상이 작은 경우가 많다.
    
- **단점: system-function overhead가 증가하여, 성능이 나빠진다는 점**이다.

### **모듈(Modules)**

- Many modern operating systems implement `loadable kernel modules(LKM)`
- 커널은 핵심적인 구성요소의 집합을 가지고 있고, **부팅 시에 또는 실행 중에 부가적인 서비스들을 모듈을 통하여 link** 한다.
- 설계 시 중요한 점은, 핵심 서비스를 제공하고 다른 서비스들은 커널이 실행되는 동안 동적으로 구현하는 것이다.
- 전체적인 결과는 각 부분이 정의되고 Protected Interface를 가진다는 점에서 계층적 구조와 비슷하다.
- 하지만, Module에서 임의의 다른 Module을 호출할 수 있다는 점에서 계층적 구조보다 유연하다.

### Hybrid Systems

Linux와 Solaris는 Monolithic 구조면서, 새로운 기능을 동적으로 추가할 수 있는 Module을 사용한다.

Windows는 Monolithic 구조면서, 동적으로 적재 가능한 커널 모듈도 지원한다.

### Structure of Darwin

- hybrid and layerd structure
- consists primarily of Mach microkernel and BSD Unix parts

![스크린샷 2023-10-10 오후 8.39.15.png](ch2%20Operating-System%20Structures%205f58cfa1a00140799a824e8988a0a01f/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-10-10_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_8.39.15.png)