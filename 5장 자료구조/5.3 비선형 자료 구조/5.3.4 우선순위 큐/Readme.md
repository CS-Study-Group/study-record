# 5.3.4 우선순위 큐

### (1) 우선순위 큐 (Priority Queue)란?

- 일반적인 큐는 FIFO(선입선출)의 구조를 가지고 있습니다.
    - 먼저 들어온 데이터가 먼저 나가는 구조입니다.
- 하지만 우선순위 큐는 들어온 순서와는 상관없이 우선순위가 높은 데이터가 먼저 나갈 수 있는 구조를 가지고 있습니다.
    - 대표적인 예시로는 CPU에서 작업 스케줄링을 하는데 사용됩니다. (처리 우선 순위가 높은 프로세스부터 처리됨)
- 우선순위 큐는 힙을 기반으로 구현이 됩니다.
    - 가지고 있는 값이 큰 것이 우선순위가 높다면 ⇒ 최대 힙으로 구현
    - 가지고 있는 값이 작은 것이 우선순위가 높다면 ⇒ 최소 힙으로 구현

<br>

### (2) 우선순위 큐를 왜 사용하는가?

- 힙을 기반으로 구현되기 때문에 데이터의 삽입, 삭제는 O(logn)의 시간 복잡도를 갖습니다.
- 그리고 우선순위대로 데이터를 꺼내서 사용하는 경우에는 O(1)의 시간 복잡도를 갖습니다.
- 단순 리스트나 배열을 사용해서 우선순위대로 정렬해서 데이터를 가져오는 경우 O(n)의 시간 복잡도를 갖기 때문에 우선순위대로 데이터가 필요한 경우에는 우선순위 큐를 사용하는 것이 더 유리할 수 있습니다.

<br>

### (3) 자바의 우선순위 큐 (Priority Queue) 활용 <번외>

- 자바의 java.utils 패키지에는 PriorityQueue가 구현되어 있습니다. 간단하게 사용해볼 수 있습니다.
    
    ```java
    import java.util.PriorityQueue;
    
    public class Test {
        public static void main(String[] args) {
            PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();
            priorityQueue.offer(25);
            priorityQueue.offer(5);
            priorityQueue.offer(4);
            priorityQueue.offer(2);
            priorityQueue.offer(23);
            priorityQueue.offer(10);
    
            StringBuilder builder = new StringBuilder();
            while (!priorityQueue.isEmpty()) {
                builder.append(priorityQueue.poll()).append(" ");
            }
            System.out.println(builder.toString());
        }
    }
    ```
    
    - 위 코드는 우선순위 큐(Priority Queue)에 무작위로 정수 데이터를 넣고, 순서대로 poll()해서 어떤 순서로 데이터에 접근할 수 있는지 알아보기 위한 코드입니다.
        - 출력 결과는 아래와 같이 나옵니다.
            
            ```java
            2 4 5 10 23 25
            ```
            
            기본적으로 값이 작은 값을 갖는 것이 우선순위가 높은 것으로 정의되어 있습니다.
            
- 값이 큰 값이 우선순위가 높은 것으로 정의하여 사용하는 우선순위 큐
    
    ```java
    import java.util.Collections;
    import java.util.PriorityQueue;
    
    public class Test {
        public static void main(String[] args) {
            PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(Collections.reverseOrder());
            priorityQueue.offer(25);
            priorityQueue.offer(5);
            priorityQueue.offer(4);
            priorityQueue.offer(2);
            priorityQueue.offer(23);
            priorityQueue.offer(10);
    
            StringBuilder builder = new StringBuilder();
            while (!priorityQueue.isEmpty()) {
                builder.append(priorityQueue.poll()).append(" ");
            }
            System.out.println(builder.toString());
        }
    }
    ```
    
    - 위 코드의 출력 결과는 아래와 같습니다.
        
        ```java
        25 23 10 5 4 2
        ```
        
        - PriorityQueue의 생성자 파라미터로 Collections.reverseOrder()만 넘겨줬는데도 우선순위가 반대로 바뀌는 것을 볼 수 있습니다.
        - PriorityQueue의 생성자 파라미터로 Comparator 객체를 받을 수 있습니다. 그럼 Collections.reverseOrder()의 반환값이 Comparator여야 가능합니다.
            
            ![image](https://user-images.githubusercontent.com/70641477/232726093-c81dcab0-74af-49b6-a13c-5633e539a914.png)
            
            - reverseOrder()의 반환 타입은 Comparator가 맞습니다. 재너릭 메서드로 정의되어 있습니다.
            - 설명을 읽어보면 reverse of the natural ordering on collection이라고 써있습니다. 기본으로 정의된 정렬(오름차순)과 반대 정렬(내림차순)을 할 수 있는 comparator를 반환한다고 되어 있습니다.
            
            ![image](https://user-images.githubusercontent.com/70641477/232726154-79f6c5df-2490-4d64-abff-9531c3268fca.png)
            
            - PriorityQueue.offer()에서 사용하는 메서드입니다. 이 siftUp()이라는 메서드 덕분에 자바의 우선순위 큐는 Comparator가 존재하지 않으면 기본 정렬 방식을 따라가고, Comparator가 존재하면 해당 Comparator에 정의된 정렬 방식으로 우선순위를 결정합니다.
