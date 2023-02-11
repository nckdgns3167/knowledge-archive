# Servlet (Server Application Let)

---

- 말 그대로 <u>**서버 앱 조각**</u>

- 클라이언트의 요청에 대한 동적인 처리를 수행하는 java 클래스.

- 실행될 때 WAS(Web Application Server)에 올라갔다가 실행이 끝나면 사라짐.

- HttpServlet 클래스를 상속하고 doPost(), doGet() 등을 재정의하여 요청에 대한 응답을 처리

- **동작 흐름**

  ![image](https://user-images.githubusercontent.com/52457180/201528988-b0ec686f-869c-4ce2-a96e-e94355d9adaf.png)

  - Web Server는 Http Request를 Web Container에게 위임.
  - 클라이언트 URL 요청이 들어오면, **Web Container가 URL 매핑을 통해 Servlet을 실행**.
  - **Servlet이 처음 실행된 것이라면 init() 메소드를 통해 Servlet을 초기화하고 메모리에 로드**.
  - **Servlet이 메모리에 적재되어있다면 Thread를 생성하고 service() 메소드를 실행해 요청에 대한 처리와 응답을 수행**.
  - service() 메소드 실행 시, 요청 Method 타입에 따라 doGet(), doPost() 메소드가 호출.
  - **요청이 끝나면 Thread는 종료되고 제거. 하지만 해당 Servlet 객체는 메모리에 계속 유지**.

- **Servlet LifeCycle**

  ![image](https://user-images.githubusercontent.com/52457180/201529270-ec6957ae-b89f-469b-b705-9f17a16aaef1.png)

  - **Web Container는 Thread의 생성과 제거를 담당**한다.
  - thead의 생성과 제거의 반복은 큰 오버헤드를 만든다.
  - 이를 위해 **Tomcat(WAS)은 Thread Pool을 만들어 오버헤드를 줄인다.**
  - 즉, **Web Container는 Servlet의 LifeCycle을 당담**한다.
  - 클라이언트의 요청이 들어왔을 때, Servlet객체 생성은 Web Container가 알아서 처리한다.
  - 개발자는 서비스 로직을 수행하는 Servlet만 개발하면 된다.

