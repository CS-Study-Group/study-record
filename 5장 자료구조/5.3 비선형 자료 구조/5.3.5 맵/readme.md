## 맵 (map)
- 이진탐색트리, 그중에서도 Red-Black Tree 구조로 구현됨

- 특정 순서(Key값을 기준으로 오른차순으로 정렬)에 따라 키와 매핑된 값의 조합으로 형성된 자료구조

- Key와 Value로 이루어진 데이터의 집합

- Key는 중복을 허용하지 않으며 Value는 중복을 허용

- 순서를 보장하지 않는 unrecorded_map 또한 존재


<br>
<br>

## Java의 맵

<br>

### Java Collection Framework

컬렉션 프레임웍이란 **"데이터 군을 저장하는 클래스틀을 표준화한 설계"** 이다.

컬렉선 프레임웍에서는 컬렉션 데이터 그룹을 크게 3가지 타입이 존재한다고 인식하고, 각 컬렉션을 다루는데 필요한 기능을 가진 3개의 인터페이스를 정의한다.

<br>

**(1) List**

순서가 있는 데이터의 집합 / 데이터의 중복을 허용

구현클래스: ArrayList, LinkedList, Stack, Vector 등

**(2) Set**

순서를 유지하지 않는 데이터의 집합 / 데이터 중복 허용하지 않음

구현 클래스: HashSet, TreeSet 등

**(3) Map**

Key와 Value의 쌍으로 이루어진 데이터의 집합 / 순서를 유지하지 않으며 Key는 중복을 허용하지 않고 Value는 중복을 허용

구현 클래스: HashMap, TreeMap, HashTable, Properties 등

<br>

컬렉션 프레임웍의 모든 컬렉션 클래스들은 List, Set, Map 중의 하나를 구현한다.

그 중 Vector와 HashTable과 같은 컬렉션 클래스는 컬렉션 프레임웍이 만들어지기 이전부터 존재했던 것이며, 현재는 각각을 개선한 ArrayList와 HashMap으로 사용하는것이 더 좋다.

<br>
<br>

### Map 인터페이스
<br>

**(1) HashMap**

HashTable의 상위 호환으로 HashTable을 HashMap에서 구현하고 있다고 보면된다.

해시함수를 통해 Map의 성질(Key와 Value의 쌍으로 이루어진 데이터)을 구현한 클래스이다.

Key와 Value를 (Object, Object)의 형태로 저장한다.

**(2) TreeMap**

Key와 Value의 쌍으로 이루어진 데이터를 저장하는데 이진탐색트리, 그중에서도 레드-블랙 트리의 형태를 구현하기 때문에 검색과 정렬이 적합하다.

HashMap과 달리 Key값을 기준으로 오름차순으로 정렬된다.

**(3) Properties**

HashMap의 구버전인 HashTable을 상속받아 구현한 것으로, Key와 Value를 (String, String)의 형태로 저장한, 보다 단순화된 클래스이다.






