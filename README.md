# Spring_Origin
## PPT
https://docs.google.com/presentation/d/1R2FhGpV9vLj5LRRL9e7PoFQjhidAhl7r/edit?usp=sharing&ouid=106583760092097027975&rtpof=true&sd=true
### Read me - 세미나 발표 식으로 진행 예정

### TodoList

[]()

1. 이론정리
2. ppt 만들기
3. 발표 스크립트 정리(필수)

---

## 주제선정이유

- Spring 프레임워크는 왜 유연성을 그리 무섭게 강조하는가?
- 공부하기 귀찮게 SOLID 원칙은 왜 생겼을까

# Spinrg은 왜 탄생하였는가

### 발표에 들어가기 전…

1. Spring 프레임워크를 이해하기 위해서는 베이스가 되는 Java 언어에 대한 기본적 이론 이해는 있어야함을
안내해야한다(Thread, Blocking I/O )

### Spring 탄생배경

- 프레임워크는 뼈대를 갖고 무언가를 만드는 일이니, 합당한 이유가 있어 Spring Framework가 탄생했을것입니다.

## 필수 사전 지식들

### 프레임워크



![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/73c2453d-5dcf-49c7-aba5-d8d0e065a8b0)



- 붕어빵 장사 달인 김모씨는 매일 붕어빵 모양을 만들어 붕어빵을 파는것이 비효율적임을 깨닫고,
붕어빵 모양 틀에 반죽 된 밀가루를 넣어 업무시간을 “단축” 시켰습니다.

### 프로세스

- 컴퓨터에서 “실행중인” 프로그램
- 쉽게 생각해보자면, 저장공간(하드디스크)에 저장되어 있는 프로그램을 메모리(RAM)에 올려서 실행하면 
프로세스이다.

### 쓰레드

- 그 프로세스에서 실행 할 수 있는 최소 작업단위가 쓰레드이다.
- 이전 컴퓨터에서는 하나의 프로세스는 하나의 작업만 처리할 수 있었음(?확인필요?)

### 웹서버의 주된 응답 포맷은 HTML이였습니다.

---



![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/5245fefd-a079-436f-bd94-9ce90fde12ba)



오래 전 웹 페이지는 전자 문서와 다를 바 없었다.해당 요청에 따른 문서를 그려주는 게 다였음)

## CGI (Common Gateway Interface)

- 웹 서버 상에서 사용자 요청에 알맞는 프로그램을 실행 시키기 위한 약속



![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/eebdbdc8-26c4-4230-98c8-b7f1ee6e6a25)




- 그렇다고 아무렇게나 생겨먹은 프로그램을 실행 할 순 없다.  서로 약속하여 만든 규약이 CGI
- 우리의 노트북 충전기를 다른 장소에 있는 멀티 탭에 꽂을 수 있는 것도 멀티 탭 제조회사가 규격(규약)에 맞게 멀티탭을 생산했기 때문이다. CGI가 이러한 규약
- Http Header에 Content-type, Http Method등을 명시해두는것도 CGI의 규약

### CGI의 특징





![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/5c0c9dc1-5389-4e10-aac6-b4b60e3c1c21)





1. Server에서 CGI 프로그램을 실행 중이라면, 다른 요청은 처리할 수 없습니다.
프로세스 단위로 실행된다는 의미
2. 매 요청시 마다 해당 CGI 프로그램이 실행됩니다.
CGI 프로그램이 끝나면 프로세스는 정리됩니다.

### Servlet





![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/d47faa18-4246-4dfc-b43a-dd0a13d8d396)





- Java 코드를 Web 환경에서 실행 할 수 있게 만들어주는 기술
Java로 구현된 CGI
- 요청이 쓰레드 단위로 실행

### Web.xml





![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/95d2a284-1149-440c-9b49-5592f452b26e)




### Servlet Container




![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/2ee13b2b-7448-48da-ad1a-d402960b8592)




1. Request, Response 객체 생성
2. 요청(url)에 알맞은 서블릿 분석
3. 찾은 서블릿에 최초 진입 시 init 메소드 생성(후에 같은 서블릿 실행 시 service 메소드 부터 호출)
4. service 메소드 실행
5. Http Method에 알맞는 do메소드 실행
6. 서블릿 파일 수정 또는 컨테이너 종료 시 destroy 메소드 실행

## WAS

그렇다면 기존 CGI는 왜 동적프로그램이 종료되면 프로세스를 종료하는 절차를 밟았는가?



![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/f422468d-3608-4350-baa5-2044ecc51a8a)



[login.pl](http://login.pl/),purchase.py등의 동적 프로그램을 띄어놓을 수 있는 데몬, 즉 관리 프로세서가 없었기 때문

그래서 탄생하게 된 동적 프로그램들만을 관리할 수 있는 전용 데몬이 WAS



![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/f1c78a5f-ef6a-4c44-9b0a-5c028f58c0ca)


- CGI 프로그램을 처리하는 서버를 따로 분리(다른 프로세스로 실행)한 방식
- CGI 프로그램과 다르게 프로세스로 계속 실행되고 있습니다.
- 그래서 우리가 WebServer(port 80) 에서 WAS(port 8080)로 포트를 통해 프로세스끼리 통신한다고 
봐도 무방합니다.
- WAS는 Servlet을 이용해 Thread 단위로 요청을 실행합니다.

### Servlet환경의 단점

다시 Servlet으로 돌아가자면,

```java
@WebServlet("/loginServlet")
public class LoginServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request,HttpServletResponse response) throws ServletException, IOException {
        // HTML 코드 작성
        String htmlRespone = "<html>";
        htmlRespone += "<h2>Your username is: " + username + "<br/>";      
        htmlRespone += "Your password is: " + password + "</h2>";    
        htmlRespone += "</html>";
         
        // return response
        writer.println(htmlRespone);
    }
}
```

### JSP


![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/66b6f173-d438-413f-a849-f3daa4fd8828)


### Servlet과 JSP를 이용한 환경의 한계점

1. Java 환경의 DB Connection 기술 문제점
2. JVM 환경의 한계점
3. 결론적으로 느리다.

### DB Connection pool

DB Connection에 소모되는 리소스 자원을 아낄 수 있음



![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/c5e1ff66-0bbc-4d8e-b480-2036b78927bd)



- Connection들을 미리 만들어 두는 것
- 이 시점 이후로 Java언어도 웹 개발에서의 시장 경쟁력이 생겼고, PHP, ASP보다 빠르거나 동급이였습니다.

### J2EE(Java 2 Enterprise Edition)

**J2EE는 자바로 기업 환경의 어플리케이션을 만드는데 필요한 스펙들을 모아둔 스펙 집합**

기업 환경에서 개발되는 애플리케이션은 좀 더 견고하게 개발되어야 하며, 복잡할 수 밖에 없음

- **Servlet :** 클라이언트가 보내는 HTTP 요청을 처리하는 서버측 자바 프로그램이며, Servlet 엔진이 있어야 합니다.
- **JSP:** HTML이나 Java 코드를 써서 사용자에게 정보를 보여 줍니다. JSP가 처음 실행될 때 Servlet 엔진이 이것을 Servlet으로 컴파일시켜서 내부적으로는 Servlet으로 동작합니다.
- **EJB(Enterprise Java Beans):** Java에서 제공하는 분산 컴포넌트 기술로 비즈니스 로직이나 데이터, 메시지를 처리할 수 있습니다.
- **RMI(Remote Method Invocation):** 프록시를 써서 원격에 있는 Java 객체의 메소드를 실행시키기 위한기술입니다.
- **JNDI(Java Naming DirectoryInterface):** 자바 기술로 만들어진 객체에 이름을 붙여 찾을 수 있도록 단일한인터페이스를 제공합니다.
- **JDBC(Java Database Connector):** 여러 종류의 데이터베이스 시스템에 접근하는 단일한 인터페이스를 제공합니다. 각각의 데이터베이스에 맞는 JDBC 드라이버가 있어야 합니다.
- **JCA(Java Connector Architecture):** 이기종 플랫폼을 통합할 수 있도록 플랫폼 독립적인 인터페이스를 제공합니다.
- **JMS(Java Message Service):** 여러 가지 메시징 시스템에 대한 플랫폼 독립적인 인터페이스를 제공합니다.

## EJB

- 인스턴스 풀링
    


![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/8bdba012-5cd2-4edf-baa8-a67733d44fc5)


    - Bean(객체)들을 미리 컨테이너 환경에 생성 해두었다가, 필요 시 객체를 반환해줌
    - Beans을 Memory 상에 미리 준비해둠
    - DB Connection도 인스턴스 풀링 기술임
- 트랜잭션 처리
    - 분산 트랜잭션을 지원함.
    - 지원 방식은 다양하나, 궁극적인 목표는 여러 호스트 환경에서도 데이터의 일관성이 유지되게 지원해줌
- Servlet 환경은 Tomcat의 Servlet 컨테이너에서 구현되어야 하는 것처럼 EJB또한 EJB 컨테이너 환경에서 구동되어야 함
- RMI(Remote Method Invocation)을 이용해 서로 다른 서버에 있는 메소드를 호출 할 수 있다.
    - 그렇다면 트랜잭션 처리가 가능하다는 장점

### EJB의 문제점

- 자바가 가진 객체지향적 구조를 무너트림
    - EJB가 지원하는 특정 기술을 사용하기 위해 상속
    
    ```java
    import javax.ejb.SessionBean;
    import javax.ejb.SessionContext;
    import javax.ejb.CreateException;
    import java.rmi.RemoteException;
    
    public class OrderServiceBean implements SessionBean {
    
        private SessionContext context;
    
        public void ejbCreate() throws CreateException {
            // EJB 초기화 코드
        }
    
        public void ejbRemove() {
            // EJB 제거 코드
        }
    
        public void ejbActivate() {
            // EJB 활성화 코드
        }
    
        public void ejbPassivate() {
            // EJB 비활성화 코드
        }
    
        public void setSessionContext(SessionContext context) {
            this.context = context;
        }
    
        public void placeOrder(Order order) throws RemoteException {
            // 비즈니스 로직이 EJB 설정에 의존
            // 예를 들어, 트랜잭션 관리 코드 등이 포함될 수 있음
        }
    }
    
    class Order {
        // 주문 관련 데이터
    }
    
    ```
    
- EJB 기술을 올바르게 다루기 위한 러닝커브가 큼
    - 무언가를 미리 만들어둔다는 것은, 미리 인스턴스에 대한 설정을 진행해두어야 한다는 의미이기도 함
    - EJB 아키텍처를 이해하기 위한 시간이 많이 소요 됨.
- 특정 컨테이너에 종속적임
    - 각 벤더 사마다 EJB컨테이너의 구현방식이 달라 서로 호환되지 않음
- EJB 환경에서의 애플리케이션을 구동하기 위해 사용하지 않는 기능들도 구현되어야 함
    - 예를 들어 어떤 비즈니스 로직에서 로깅작업을 진행하려면, 로그 라이브러리 관련된 설정이 
    비즈니스 코드파일에 침투가 된다.
- 객체지향적인 성격을 망가트리는 기술침투
    - 위에서 언급한 환경 구성 및 등으로 인해  특정기술에 의존성을 띄게됨.
- 결론적으로 개발자에게 편의성을 제공해주려다, 그 목적성이 무너지게 된 프레임워크

### POJO(Plain Old Java Object)

- 직역한다면, 오래된 방식의 간단한 자바 오브젝트,
한마디로 순수한 자바 오브젝트를 말한다.
- 특정 기술과 환경에 종속되지 않고 순수한 자바 오브젝트로만 이루어진 오브젝트

```java
public class MessageForm extends ActionForm {
    String message;

    public String getMessage() {
        return message;
    }

    public void setMessage(String message) {
        this.message = message;
    }
}

public class MessageAction extends Action {
    public ActionForward execute(ActionMapping mapping, ActionForm form,
        HttpServletRequest request, HttpServletResponse response)
        throws Exception {

        MessageForm messageForm = (MessageForm) form;
        messageForm .setMessage("Hello World");

        return mapping.findForward("success");
    }
}
```

- 외부 라이브러리인 Struts 웹 프레임워크  Action 클래스를 상속받고 있는 소스
만약 Structs를 거둬내고 다른 프레임워크를 사용하게 된다면, 해당 비즈니스 로직은 새로 구현해야함.




![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/3a6138ae-cef1-4ec3-89bf-19e13487f9c8)




### IOC ( Inversion of Control)



![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/1b49bbf6-eb6d-4575-86ea-992cffb75067)


- **개발자가 제어해야할 요소들을 Spring Framework에서 대신 제어**
- DI를 통해 IOC Container에서 객체들을 관리합니다.

### DI ( Dependency Injection)

- 의존성 주입

```java
//IOC Container에서 관리 가능한 컴포넌트임을 명시
@Controller
public class MenuController {
	private final MenuService  menuService;
	//의존성 주입 
	@Autowired
	public MenuController(MenuService menuService) {
		this.menuService = menuService;
	}

}

```


![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/11ce7305-3391-47ff-8b74-04a65d68f9db)



### PSA (**Portable Service Abstraction)**

- 직역하면 편리한 서비스 추상화
- Transactional Annotation



![Image](https://github.com/OHLPstudy/Spring_Origin/assets/49707719/dc752d93-d323-42c8-9272-3f216292c4f7)



- 우리가 ORM을 JPA, JDBC, Mybatis 등으로 변경해도 Transactional 어노테이션은 동일하게 사용 가능
트랜잭션 계층은 각각의 TxManager(추상화 계층을) 통해 가져올 수 있는데,
인터페이스인 PlatfromTransactionManager를 사용하면 사용하는 기술(JPA -> Mybatis)이 변경된다 하여도,
비즈니스 로직의 변경점 없이 트랜잭션 정보를 가져올 수 있음
*내용이 상당히 헷갈려 참고 사이트 첨부
https://sabarada.tistory.com/127﻿
### AOP

```java
public void method_name() throw Exception {
    TransactionalSynchronizationManager.initSunchronization();
    Connection c = DataSourceUtils.getConnection(dataSource);
    try {
        // 3. DB 쿼리 실행
        c.commit();
    } catch(Exception e) {
        c.rollback();
        throw e;
    } finally {
        DatasourceUtils.releaseConnection(c, dataSource);
        TransactionSynchronizationManager.unbindResource(dataSource);
        TransactionSynchronizationManager.clearSynchronization();
    }
}
```

“3. DB 쿼리실행” 주석처리에 실제 우리의 비즈니스 로직이 들어간다.

해당 로직으로 인해 commit 작업에서 예외 발생 시 rollback이 가능한 것

또한 finally 소스쪽에서 connection 관련 연결된 리소스를 해제하는 방법이 작성되어 있어 개발자는 Connection에 대한 해제작업을 신경쓰지 않아도 된다.

## Hibernate, Spring

### Spring 구조에 대한 이미지 위주 설명

- 이미지
    - Description


### 출처

### Spring

[[[Spring] 스프링 프레임워크(Spring framework)의 탄생 배경 (feat. CGI, Servlet, JSP, J2EE, EJB) - 2편](https://jhyonhyon.tistory.com/27)](https://jhyonhyon.tistory.com/27)

## POJO

[[[Spring] POJO란 무엇인가?](https://ittrue.tistory.com/211)](https://ittrue.tistory.com/211)

### EJB

[[홍차넷 - EJB 를 아시나요? (1)](https://redtea.kr/free/8055)](https://redtea.kr/free/8055)

### PSA

[[[Spring] Spring의 핵심기술 PSA - 개념과 원리](https://sabarada.tistory.com/127)](https://sabarada.tistory.com/127)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e0a05103-106f-4c10-a5c2-352af7fa739b/d3627bd3-7214-4cc7-b33f-493c8a10355e/Untitled.png)
