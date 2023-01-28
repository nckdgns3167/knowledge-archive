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



