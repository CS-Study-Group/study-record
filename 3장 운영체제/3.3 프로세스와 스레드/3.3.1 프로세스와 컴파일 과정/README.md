# 3.3.1 프로세스의 컴파일 과정

## 프로그램과 프로세스

### 프로그램

- 컴퓨터에서 실행될 때 특정 작업을 수행하는 일련의 명령어들의 모음.
- 명령어들의 모음일뿐 프로그램 자체만으로는 무언가 일을 할 수 있는게 아니다.
- exe확장자의 실행파일들이 프로그램.

<img width="735" alt="Untitled" src="https://user-images.githubusercontent.com/80507195/234028570-f4c1d58e-d152-422c-95f5-5e0ce1196e12.png">

### 프로세스

- 프로그램을 구동하여 프로그램 자체와 프로그램 상태가 메모리상에서 실행되는 작업.
- 프로그램이 메모리상으로 올라가면 프로세스가 되는 인스턴스화 과정이 일어난다.
    
   <img width="380" alt="Untitled 1" src="https://user-images.githubusercontent.com/80507195/234028213-ba15ccad-92a2-4212-aedb-afd6038821ce.png">

ex) 피시카카오톡에 로그인을하고, zoom회의실에 참여하고, 플래너구성을 엑셀로 작업한다했을때

프로그램 - 카카오톡(pc버전), zoom, 엑셀

프로세스 - 카카오톡pc로그인하는작업, zoom회의실 참여작업, 플래너구성작업

# C언어상의 컴파일과정

<img width="328" alt="Untitled 2" src="https://user-images.githubusercontent.com/80507195/234028744-d52886ea-5709-4f5a-baf6-08d606d0cd42.png">

## 전처리 과정(preprocessing)

- 본격적으로 컴파일 하기 전에 처리할 작업들을 일컫는다.
- 외부에 선언된 다양한 소스 코드, 라이브러리 포함(ex. #include)
- 프로그래밍의 편의를 위해 작성된 매크로변환(ex. #define)
- 컴파일할 영역 명시(ex. #if, #ifdef)

## 컴파일 과정(compiling)

- 전처리가 완료 되어도 여전히 소스코드인상태다
- 전처리 완료된 소스 코드를 오류 처리 및 최적화 작업을 통해 어셈블리어로 변환한다.
- 어셈블리어 : 컴퓨터 본래의 언어에 가장 가까운 언어(저급 언어)

## 어셈블 과정(assembling)

- 어셈블리어를 기계어로 변환
- 목적 코드(object file)를 포함하는 목적 파일이 된다.

### 목적파일 vs 실행파일

- 목적 파일과 실행 파일은 둘다 기계어로 이루어진 파일
- 하지만 둘은 엄연히 다르다.
- 목적파일(.o) —> 링킹(linking) —> 실행파일(.exe)

## 링킹과정(linking)

- 오브젝트파일 및 프로그램에서 사용된 라이브러리를 묶어주는 작업.
- 링킹과정을 거치면 실행 가능한 exe파일이 생성됨.

<img width="682" alt="Untitled 3" src="https://user-images.githubusercontent.com/80507195/234028966-fdca978f-5db6-47c5-99ec-7c74c659ef09.png">

# 자바에서의 컴파일 과정

<img width="617" alt="Untitled 4" src="https://user-images.githubusercontent.com/80507195/234029270-131633c8-6f2c-4e94-ac3c-28de4405e4e0.png">


- JAVA는 하드웨어, 운영체제에 상관없이 컴파일된 코드가 독립적.
    - JVM : 컴파일된 코드(바이트코드)를 실행시켜주는 가상의 공간
- 어느 플랫폼이든 작성한 소스를 변경할 필요없이 실행시킬 수 있다.

### 

<img width="731" alt="Untitled 5" src="https://user-images.githubusercontent.com/80507195/234029458-c4fe8ab5-545e-4116-9110-14f8955811a8.png">

1. 개발자가 자바 소스코드를 작성(.java)
2. 자바 컴파일러가 자바 소스파일을 컴파일한다. 이때 나오는 파일은 자바 바이트 코드인 클래스 파일 (.class).
    - JVM은 읽어들일수있으나, 컴퓨터가 직접적으로는 못읽어들이는 상태.
3. 컴파일된 바이트 코드를 JVM 클래스로더에 전달한다.
4. 클래스 로더는 동적로딩을 통해 필요한 클래스들을 로딩 및 링크하여 런타임 데이터 영역인 JVM의 메모리에 올린다.
    - 클래스 로더상의 세부적인 동작들
        - 로드 :  클래스 파일을 가져와 JVM메모리에 업로드.
        - 검증 :  자바 언어 명세(Java Language Specifition)및 JVM 명세에 명시된 대로 구성되어있는지 검사
        - 준비 : 클래스가 필요로 하는 메로리를 할당한다.(field, method, interface)
        - 분석 :  클래스 constant pool 내 모든  symbolic reference를 direct reference로 변경한다.
        - 초기화 : 클래스 변수들을 적절한 값으로 초기화(static field)
5. JVM의 실행엔진은 JVM 메모리에 올라온 바이트코드(클래스파일)들을 명령어 단위로 하나씩 가져와 실행한다.
    - 실행 엔진은 두가지 방식
        - 인터프리터
            - 바이트 모드를 하나씩 읽어서 실행한다
            - 한줄씩의 실행은 빠르지만 전체적인 실행속도는 느리다.
        - JIT 컴파일러(Just-In-TIme Compiler)
            - 인터프리터의 단점을 보완하기 위해 도입된방식
            - 바이트 코드 전체를 컴파일하여 바이너리 코드로 변경.
                
                이후 해당 메서드를 더이상 인터프리팅 하지않고,
                바이너리코드로 직접 실행
                
            - 전체적인 실행속도는 인터프리팅보다 빠른편이다.
        
        <img width="315" alt="Untitled 6" src="https://user-images.githubusercontent.com/80507195/234029675-44cf6512-883e-4fe4-964a-9d8a839782e1.png">

        
        # 참고자료
        
        [[운영체제] 프로그램과 프로세스의 차이점](https://breathtaking-life.tistory.com/100)
        
        [Java 컴파일 과정](https://jungeu1509.github.io/interview/JAVA_Compile/)
        
        [알기쉽게 정리한 JAVA의 컴파일과정 및 JVM 메모리 구조, JVM GC](https://aljjabaegi.tistory.com/387)
        
        [https://gyoogle.dev/blog/computer-language/Java/컴파일 과정.html](https://gyoogle.dev/blog/computer-language/Java/%EC%BB%B4%ED%8C%8C%EC%9D%BC%20%EA%B3%BC%EC%A0%95.html)
        
        [https://www.youtube.com/watch?v=MYKFLepF1UM](https://www.youtube.com/watch?v=MYKFLepF1UM)
