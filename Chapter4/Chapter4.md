# Chapter 4. 스택, 큐, 덱

## 1. 개념 설명

* `스택 (Stack)`은 마지막에 저장한 것을 먼저 꺼내는 자료구조다. (`LIFO`: `Last In First Out`)

    * 한쪽 끝에서만 데이터를 삽입, 삭제할 수 있다.

    * 시간 복잡도는 다음과 같다.

        * 삽입 : `O(1)` , 삭제 : `O(1)`

* `큐 (Queue)`는 먼저 저장한 것을 먼저 꺼내는 자료구조다. (`FIFO`: `First In First Out`)

    * 한쪽 끝에서만 데이터를 삽입하고 다른 한쪽 끝에서만 삭제할 수 있다.

    * 시간 복잡도는 다음과 같다.

        * 삽입 : `O(1)` , 삭제 : `O(1)`

* `덱 (Deque)`은 양쪽 끝에서 데이터를 삽입하고 삭제할 수 있는 자료구조다.

    * `덱`은 한 쪽의 연산만 사용하면 `Stack`이 되고 두 연산만 사용하면 `Queue`가 된다.

        * 즉, 덱은 `Stack`과 `Queue`의 특징을 모두 가지고 있다.

    * 덱은 배열 또는 연결 리스트로 구현할 수 있다.

    * 시간 복잡도는 다음과 같다.

        * 삽입 : `O(1)` , 삭제 : `O(1)`

## 2. 연습 문제

### 2-1. 프로그래머스 - 올바른 괄호

```java
import java.util.*;

class Solution {
    boolean solution(String s) {
        Stack<Character> stack = new Stack<>();

        for (char ch : s.toCharArray()) {
            if (ch == ')') {
                if (!stack.isEmpty() && stack.peek() == '(')
                    stack.pop();
                else
                    return false;
            } else {
                stack.push(ch);
            }
        }

        return stack.isEmpty();
    }
}
```

### 2-2. Codility - CyclicRotation

* 덱 (Deque)으로 풀이하기

```java
public class Solution {
    public int[] solution(int[] A, int K) {
        Deque<Integer> deque = new LinkedList<>();
        for (int num : A) {
            deque.add(num);
        }

        // K번 반복하며 마지막 요소를 빼서 첫 번째에 다시 삽입한다.
        for (int i = 0; i < K; i++) {
            int lastNum = deque.removeLast();
            deque.addFirst(lastNum);
        }

        return deque.stream()
                .mapToInt(Integer::intValue)
                .toArray();
    }
}
```


