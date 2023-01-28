# Java 메모장

---

### Map 인터페이스의 3가지 구현체 비교

- HashMap: 

> - key와 value에 null을 허용한다.
> - 동기화를 보장하지 않는다.
> - thread-safe하지 않아, `싱글 쓰레드 환경`에서 사용하는 게 좋다.
> - 동기화 처리를 하지 않기 때문에, 데이터를 탐색하는 속도가 빠르다.
> - 데이터를 찾는 속도는 빠르지만, 신뢰성과 안정성이 떨어진다.

- Hashtable

> - key와 value에 null을 허용하지 않는다.
> - 동기화를 보장한다.
> - thread-safe하기 때문에, `멀티 쓰레드 환경`에서 사용할 수 있다.
> - 데이터를 다루는 메소드(get(), put(), remove() 등)에 `synchronized` 키워드가 붙어 있다. 
> - 해당 키워드는 메소드를 호출하기 전에 쓰레드간 동기화 락을 건다. 그래서 멀티 쓰레드 환경에서도 데이터의 무결성을 보장한다.
> - 그러나, 쓰레드간 동기화 락은 매우 느린 동작이라는 단점이 있다.

- ConcurrentHashMap

> - key와 value에 null을 허용하지 않는다.
> - 동기화를 보장한다.
> - thread-safe하기 때문에, `멀티 쓰레드 환경`에서 사용할 수 있다.
> - 이 구현체는 HashMap의 동기화 문제를 보완하기 위해 나타났다.
> - 동기화 처리를 할 때, 어떤 Entry를 조작하는 경우에 해당 Entry에 대해서만 락을 건다. 그래서 HashTable보다 데이터를 다루는 속도가 빠르다.
> - 즉, Entry 아이템별로 락을 걸어 멀티 쓰레드 환경에서의 성능을 향상시킨다.

- **결론**

> - 싱글 쓰레드 환경 👉 HashMap
> - 멀티 쓰레드 환경 👉 HashTable보다 데이터 다루는 속도가 빠른 ConcurrentHashMap 

- References
  - https://tecoble.techcourse.co.kr/post/2021-11-26-hashmap-hashtable-concurrenthashmap/

---

### 래퍼 클래스(포장 클래스), 프리미티브 타입(원시 타입)

- 사용 용도에 따라 다르겠지만 일반적으로는 **primitive type**을 많이 사용한다. **wrapper**의 경우 결국 객체를 생성하는 것인데, 굳이 객체가 필요한 경우가 없거나 **null**값을 반환할 필요가 없다면 객체를 생성하지 않고 **primitive type**을 사용하는 것이 메모리의 측면에서 효율적이다.

  또한 **wrapper**의 경우 객체이기 때문에 **==** 연산이 아닌 **equals()** 메소드를 이용해서 값을 비교해야 한다. 그렇기 때문에 직관적으로 값을 비교함에 있어서도 **primitive**가 편리하다.

- **Boxing과** **UnBoxing**

  - **Boxing**이란 원시 타입을 포장 클래스로 변환하는 것입니다.
  - **UnBoxing**은 포장 클래스를 원시 타입으로 변환하는 것입니다.
  - JDK 1.5 부터는 **autoBoxing, autoUnBoxing** 이라는 것이 적용되어 자동적으로 **primitive type과** **wrapper class**를 형변환한다.





