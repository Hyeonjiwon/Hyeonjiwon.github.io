---
title: '[Programmers] 코딩테스트 연습 Level 1' 
excerpt: "Level 1"
categories:
    - Algorithm
    - JAVA
    - Python

tag:
    - Programmers
    - Algorithm
    - java
    - python

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2021-04-02T19:00:00+09:00

toc: true   #Table Of Contents 목차 

toc_sticky: true
---

## K번째수

__문제__

배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

1. array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
2. 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
3. 2에서 나온 배열의 3번째 숫자는 5입니다.

배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

__제한사항__

- array의 길이는 1 이상 100 이하입니다.
- array의 각 원소는 1 이상 100 이하입니다.
- commands의 길이는 1 이상 50 이하입니다.
- commands의 각 원소는 길이가 3입니다.

__입출력 예__

| array                 | commands                          | return    |
| --------------------- | --------------------------------- | --------- |
| [1, 5, 2, 6, 3, 7, 4] | [[2, 5, 3], [4, 4, 1], [1, 7, 3]] | [5, 6, 3] |

__풀이__

```java
import java.util.*;

class Solution {
    public static int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

        for (int i = 0; i < commands.length; i++) {
            ArrayList<Integer> list = new ArrayList<Integer>();

            for (int j = commands[i][0]; j <= commands[i][1]; j++) {
                list.add(array[j-1]);
            }

            Collections.sort(list);
            int k = list.get(commands[i][2]-1);
            answer[i] = k;
        }

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int[] array = {1, 5, 2, 6, 3, 7, 4};
        int[][] commands = { {2, 5, 3}, {4, 4, 1}, {1, 7, 3} };

        int[] result = solution(array, commands);

        for (int i: result) {     
            System.out.println(i); 
        }
    }
}
```

<br>

## 완주하지 못한 선수

__문제__

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

__제한사항__

- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.

__입출력 예__

| participant                                       | completion                               | return   |
| ------------------------------------------------- | ---------------------------------------- | -------- |
| ["leo", "kiki", "eden"]                           | ["eden", "kiki"]                         | "leo"    |
| ["marina", "josipa", "nikola", "vinko", "filipa"] | ["josipa", "filipa", "marina", "nikola"] | "vinko"  |
| ["mislav", "stanko", "mislav", "ana"]             | ["stanko", "ana", "mislav"]              | "mislav" |

__풀이__

```java
import java.util.*;

class Solution {
    public static String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String, Integer> hm = new HashMap<String, Integer>();

        for (String name : participant) {
            hm.put(name, hm.getOrDefault(name, 0) + 1);
        }

        for (String name : completion) {
            if(hm.containsKey(name)){
                hm.put(name, hm.get(name) - 1);
            }
        }

        for (String name : hm.keySet()) {
            if(hm.get(name) == 1) {
                answer = name;
            }
        }

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        String[] participant = {"mislav", "stanko", "mislav", "ana"};
        String[] completion = {"stanko", "ana", "mislav"};
        
        System.out.println(solution(participant, completion)); 
    }
}
```

<br>

## 2016년

__문제__

2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? 두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. 요일의 이름은 일요일부터 토요일까지 각각  [ SUN, MON, TUE, WED, THU, FRI, SAT ]

입니다. 예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 "TUE"를 반환하세요.

__제한사항__

- 2016년은 윤년입니다.
- 2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다)

__입출력 예__

| a   | b   | result |
| --- | --- | ------ |
| 5   | 24  | "TUE"  |

__풀이__

```java
class Solution {
    
    public static String solution(int a, int b) {
        String answer = "";

        int[] month = { 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
        String[] dayOfweek = { "THU", "FRI", "SAT", "SUN", "MON", "TUE", "WED" };

        int d = 0, result = 0;

        for (int i = 0; i < (a -1); i++) {
            d = d + month[i];
       }

        result = ((d + b) % 7);
        answer = dayOfweek[result];

        return answer;
    }
}
```

- datetime.datetime().weekday()
  
```python
import datetime

def solution(a, b):
    day = {0:"MON", 1:"TUE", 2:"WED", 3:"THU", 4:"FRI", 5:"SAT", 6:"SUN"}
    return day[datetime.datetime(2016, a, b).weekday()]
```

<br>

## 모의고사

__문제__

수포자는 수학을 포기한 사람의 준말입니다. 수포자 삼인방은 모의고사에 수학 문제를 전부 찍으려 합니다. 수포자는 1번 문제부터 마지막 문제까지 다음과 같이 찍습니다.

1번 수포자가 찍는 방식: 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, ...
2번 수포자가 찍는 방식: 2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5, ...
3번 수포자가 찍는 방식: 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, ...

1번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers가 주어졌을 때, 가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수를 작성해주세요.

__제한사항__

- 시험은 최대 10,000 문제로 구성되어있습니다.
- 문제의 정답은 1, 2, 3, 4, 5중 하나입니다.
- 가장 높은 점수를 받은 사람이 여럿일 경우, return하는 값을 오름차순 정렬해주세요.

__입출력 예__

| answers     | return  |
| ----------- | ------- |
| [1,2,3,4,5] | [1]     |
| [1,3,2,4,2] | [1,2,3] |

__풀이__

```java
import java.util.ArrayList;

class Solution {
    public static int[] solution(int[] answers) {
        int[] answer = {};

        int[] tnvhwk1 = { 1, 2, 3, 4, 5, 1, 2, 3, 4, 5 }; 
        int[] tnvhwk2 = { 2, 1, 2, 3, 2, 4, 2, 5 }; 
        int[] tnvhwk3 = { 3, 3, 1, 1, 2, 2, 4, 4, 5, 5 }; 

        int[] count = new int[3];

        for (int i = 0; i < answers.length; i++) {
            if ((tnvhwk1[i % tnvhwk1.length]) == answers[i]) {
                count[0]++;
            }
            if (tnvhwk2[i % tnvhwk2.length] == answers[i]) {
                count[1]++;
            }
            if (tnvhwk3[i % tnvhwk3.length] == answers[i]) {
                count[2]++;
            }
        }

        ArrayList<Integer> list = new ArrayList<Integer>();

        // 최고 점수 찾기
        int max = Math.max(Math.max(count[0], count[1]), count[2]); 

        // 최고점자만 add 
        if(max==count[0]) list.add(1); 
        if(max==count[1]) list.add(2);
        if(max==count[2]) list.add(3);

        System.out.println("list " + list);
        
        // answer 리스트 길이만큼 초기화
        // answer = list.toArray(new Int[list.size()]); => toArray는 Object 형식으로 반환
        // Stream API를 사용하면 실행 시간이 오래걸림
        answer = list.stream().mapToInt(i -> i).toArray();

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int[] answers = { 1, 2, 3, 4, 5 };

        int[] answer = solution(answers);

        for (int i = 0; i < answer.length; i++) {
            System.out.println(answer[i]); 
        }
    }
}
```

<br>

## 수박수박수박수박수박수?

__문제__

길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.

__제한사항__

- n은 길이 10,000이하인 자연수입니다.

__입출력 예__

| n   | return     |
| --- | ---------- |
| 3   | "수박수"   |
| 4   | "수박수박" |

__풀이__

```java
class Solution {
    public static String solution(int n) {
        String answer = "";

        StringBuilder sb = new StringBuilder();

        for (int i = 0; i <= (n/2); i++) {
            sb.append("수박");
        }
        
        answer = sb.substring(0, n);
        
        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int n = 3;

        System.out.println(solution(n));
    }
}
```

```python
def solution(n):
    s = '수박'
    answer = ''
    
    for i in range(n):
        if i%2 == 0:
            answer += s[0]
            
        elif i%2 == 1:
            answer += s[1] 
    
    return answer
```

>```python
> s = "수박" * n
> return s[:n]
>```

<br>

## 문자열 다루기 기본

__문제__

문자열 s의 길이가 4 혹은 6이고, 숫자로만 구성돼있는지 확인해주는 함수, solution을 완성하세요. 예를 들어 s가 "a234"이면 False를 리턴하고 "1234"라면 True를 리턴하면 됩니다.

__제한사항__

- s는 길이 1 이상, 길이 8 이하인 문자열입니다.

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```java
class Solution {
    public boolean solution(String s) {
        boolean answer = true;        
        
        if (s.length() == 4 || s.length() == 6) {
            answer = s.matches("^[0-9]*$");
            return answer;
        } 
        else {
            return false;
        }
    }
}
```

```python
def solution(s):
    if s.isdigit() and (len(s) == 4 or len(s) == 6):
        return True
    else:
        return False
```

> ```python
> s.isdigit() and len(s) in (4, 6)
> ```

<br>

## 두 개 뽑아서 더하기

__문제__

정수 배열 numbers가 주어집니다. numbers에서 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담아 return 하도록 solution 함수를 완성해주세요.

__제한사항__

- numbers의 길이는 2 이상 100 이하입니다.
- numbers의 모든 수는 0 이상 100 이하입니다.

__입출력 예__

| numbers     | result        |
| ----------- | ------------- |
| [2,1,3,4,1] | [2,3,4,5,6,7] |
| [5,0,2,7]   | [2,5,7,9,12]  |

__풀이__

```java
import java.util.TreeSet;

class Solution {
    public static int[] solution(int[] numbers) {
        int[] answer = {};
        TreeSet<Integer> set = new TreeSet<Integer>();

        for (int i = 0; i < numbers.length; i++) {
            for (int j = i+1; j < numbers.length; j++) {
                set.add(numbers[i] + numbers[j]);
            }
        }

        answer = set.stream().mapToInt(i -> i).toArray();
        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int[] numbers = {2};

        for (int i : solution(numbers)) {
            System.out.print(i + " ");
        }
    }
}
```

<br>

## 자연수 뒤집어 배열로 만들기

__문제__

자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요. 예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

__제한사항__

- n은 10,000,000,000이하인 자연수입니다.

__입출력 예__

| n     | return      |
| ----- | ----------- |
| 12345 | [5,4,3,2,1] |

__풀이__

```java
class Solution {
    public static int[] solution(long n) {
        int[] answer = {};
        StringBuilder s = new StringBuilder(String.valueOf(n));
        String rev = s.reverse().toString();

        answer = new int[rev.length()];

        for (int i = 0; i < rev.length(); i++) {
             answer[i] = rev.charAt(i) - '0';
        }

        return answer;
        
        /** 풀이1 > 속도 3 ** 
        answer = s.reverse().chars().map(x -> x - '0').toArray(); // 속도가 넘 느림
        answer = Stream.of(rev.split("")).mapToInt(Integer::parseInt).toArray();
        */

        /** 풀이 2 > 속도 2 **
        int [] rev = s.reverse().chars().toArray();
        answer = new int[rev.length];
        for (int i = 0; i < rev.length; i++) {
            answer[i] = rev[i] - '0';
       }
        */

        /** 풀이 3 **
        char[] s = new StringBuilder(String.valueOf(n)).reverse().toString().toCharArray();
        answer = new int[s.length];

        for (int i = 0; i < s.length; i++) {
             answer[i] = s[i] - '0';
        }
        */
    }

    public static void main(String[] args) { 
        // test case
        int n = 12345;

        for (int i : solution(n)) {
            System.out.print(i + " ");
        }
    }
}
```

```python
def solution(n):
    n_list = list(reversed(list(str(n))))
    return list(map(int, n_list))
```

<br>

## 가운데 글자 가져오기

__문제__

단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

__제한사항__

- s는 길이가 1 이상, 100이하인 스트링입니다.

__입출력 예__

| s       | return |
| ------- | ------ |
| "abcde" | "c"    |
| "qwer"  | "we    |

__풀이__

```java
class Solution {
    public static String solution(String s) {
        String answer = "";
        int len = s.length();

        if (len % 2 == 0) {
            answer = s.substring((len/2)-1, (len/2)+1);
        } else {
            answer = s.substring((len/2), (len/2)+1);
        }

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        String s = "abced";
        String ss = "qwer";

        System.out.println(solution(s));
    }
}
```

<br>

## 두 정수 사이의 합

__문제__

두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, solution을 완성하세요.
예를 들어 a = 3, b = 5인 경우, 3 + 4 + 5 = 12이므로 12를 리턴합니다.

__제한사항__

- a와 b가 같은 경우는 둘 중 아무 수나 리턴하세요.
- a와 b는 -10,000,000 이상 10,000,000 이하인 정수입니다.
- a와 b의 대소관계는 정해져있지 않습니다.

__입출력 예__

| a   | b   | return |
| --- | --- | ------ |
| 3   | 5   | 12     |
| 3   | 3   | 3      |
| 5   | 5   | 12     |

__풀이__

```java
class Solution {
    public static long solution(int a, int b) {
        long answer = 0;
        
        for (int i = Math.min(a, b); i <= Math.max(a, b); i++) {
            answer = answer + i;
        }
        
        /*
        if (a > b) {
            for (int i = b; i <= a; i++) {
                answer = answer + i;
            }
        }
        else {
            for (int i = a; i <= b; i++) {
                answer = answer + i;
            }
        }
        // *
        for (int i = ((a > b) ? b : a); i <= ((a > b) ? a : b); i++) {
            answer = answer + i;
        }
        */
    }

    public static void main(String[] args) { 
        // test case
        int a = 5, b = 3;

        System.out.println(solution(a, b));
    }
}
```

<br>

## 같은 숫자는 싫어

__문제__

배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져 있습니다. 이때, 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. 단, 제거된 후 남은 수들을 반환할 때는 배열 arr의 원소들의 순서를 유지해야 합니다. 예를 들면,

- arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
- arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.

배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.

__제한사항__

- 배열 arr의 크기 : 1,000,000 이하의 자연수
- 배열 arr의 원소의 크기 : 0보다 크거나 같고 9보다 작거나 같은 정수

__입출력 예__

| arr             | answer    |
| --------------- | --------- |
| [1,1,3,3,0,1,1] | [1,3,0,1] |
| [4,4,4,3,3]     | [4,3]     |

__풀이__

```java
import java.util.*;

class Solution {
    public static int[] solution(int []arr) {
        int[] answer = {};
        ArrayList<Integer> list = new ArrayList<Integer>();

        list.add(arr[0]);

        for (int i = 1; i < arr.length; i++) {
            if (arr[i-1] != arr[i]) {
                list.add(arr[i]);
            }
        }

        answer = new int[list.size()];
        int idx = 0;
        
        for (int i : list) {
            answer[idx] = i;
            idx++;
        }

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int[] arr = { 1, 1, 3, 3, 0, 1, 1 };

        for (int i : solution(arr)) {
            System.out.println(i);
        }
    }
}
```

<br>

## 서울에서 김서방 찾기

__문제__

String형 배열 seoul의 element중 "Kim"의 위치 x를 찾아, "김서방은 x에 있다"는 String을 반환하는 함수, solution을 완성하세요. seoul에 "Kim"은 오직 한 번만 나타나며 잘못된 값이 입력되는 경우는 없습니다.

__제한사항__

- seoul은 길이 1 이상, 1000 이하인 배열입니다.
- seoul의 원소는 길이 1 이상, 20 이하인 문자열입니다.
- "Kim"은 반드시 seoul 안에 포함되어 있습니다.

__입출력 예__

| seoul             | return              |
| ----------------- | ------------------- |
| [ "Jane", "Kim" ] | "김서방은 1에 있다" |

__풀이__

```java
class Solution {
    public static String solution(String[] seoul) {
        String answer = "";
        int num = 0; 

        for (String string : seoul) {
            if (string.equals("Kim")) {
                answer = "김서방은 " + String.valueOf(num) + "에 있다";
            }
            num++;
        }
        return answer;
    }
}
```

```python
def solution(seoul):
    answer = ''
    
    for i in range(len(seoul)):
        if "Kim" in seoul[i]:
            return "김서방은 " + str(i) + "에 있다"
```

> ```python
> return "김서방은 {}에 있다".format(seoul.index('Kim'))
> ```

<br>

## x만큼 간격이 있는 n개의 숫자

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python
import time
start = time.time()  # 시작 시간

def solution(x, n):
    answer = []
    tmp = 0

    for i in range(n):
        tmp = tmp + x
        answer.append(tmp)

    return answer

def main(): 
    print(solution(2, 5))

if __name__ == '__main__':
    main()
    print("time :", time.time() - start)  # 실행 시간
```

<br>

 ##  로또의 최고 순위와 최저 순위

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python 
import time
start = time.time()  # 시작 시간

def solution(lottos, win_nums):
    # 배열 길이가 6보다 클 경우
    if (len(lottos) > 6) or (len(win_nums) > 6):
        raise Exception('Items exceeds the maximum allowed length of 6')

    else:
        answer = []
        # 맞춘 개수 : 순위
        dict =  {0:6, 1:6, 2:5, 3:4, 4:3, 5:2, 6:1}
        set_lottos = set(lottos)
        set_winNum = set(win_nums)

        min = len(set_lottos.intersection(set_winNum)) # 교집합
        max = min + lottos.count(0) # 0 개수 count

        # max = len(set(lottos) & set(win_nums)) + lottos.count(0)
        # min = len(set(lottos) & set(win_nums))

        return [dict.get(max, "?"), dict.get(min, "?")] # time : 0.0006847381591796875
        # return [dict[max], dict[min]] # time : 0.0009970664978027344

"""
def switch(key):
    # 맞춘 개수 : 순위
    answer = {1:6, 2:5, 3:4, 4:3, 5:2, 6:1}.get(key, "?")
    return answer
"""

def main():
    # 민우가 구매한 로또 번호
    lottos = [44, 1, 0, 0, 31, 25]
    # 당첨 번호
    win_nums = [31, 10, 45, 1, 6, 19]
    
    print(solution(lottos, win_nums))


if __name__ == '__main__':
    main()
    print("time :", time.time() - start)  # 실행 시간
```

<br>

## 신규 아이디 추천

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python
import time
start = time.time()  # 시작 시간 저장

import re

def solution(new_id):
    # 배열 길이
    if (len(new_id) < 0) or (len(new_id) > 1000):
        raise Exception('Items exceeds the maximum allowed length')

    # 1
    new_id = new_id.lower()
    
    # 2
    new_id = re.sub('[^0-9a-z\-_.]', '', new_id)

    # 3
    new_id = re.sub('[.]{1,}', '.', new_id)
    
    # 4
    if len(new_id) >= 2:
        if new_id.startswith('.'):
            new_id = new_id[1:]

    if new_id.endswith('.'):
        new_id = new_id[:-1]

    # 5
    if not new_id:
        new_id = new_id.replace("", "a")

    # 6
    if len(new_id) > 15:
        new_id = new_id[:15]

        if new_id.endswith('.'):
            new_id = new_id[:-1]
    
    # 7  
    #while len(new_id) < 3:
    #    new_id = new_id + new_id[-1]

    new_id+=new_id[-1]*(3-len(new_id))

    return new_id

def main():
    id = "...!@BaT#*..y.abcdefghijklm"    
    print(solution(id))

if __name__ == '__main__':
    main()
    print("time :", time.time() - start)  # 실행 시간

```

<br>

## 직사각형 별찍기

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python 
a, b = map(int, input().strip().split(' '))

for i in range(b):
    print(('*' * a))
```

<br>

## 콜라츠 추측

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python
def solution(num):
    answer = 0

    while num > 1:
        if num % 2 == 0:
            num = num/2

        else:
            num = (num * 3) + 1

        if (answer <= 500):
            answer = (answer + 1) 
    
        else: 
            return -1
        
    return answer
```

```python
def solution(num):
    answer = 0
    result = 0
    
    while num != 1:
        if num % 2 == 0:
            num /= 2
        elif num % 2 == 1:
            num = (num * 3) + 1
        
        answer += 1
        
        if answer == 500:
            return -1
    
    return answer
```

<br>

## 평균 구하기  

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python
import numpy as np

def solution(arr):
    answer = 0
    answer = sum(arr)/len(arr)
    return answer

    # return np.mean(arr) # 속도가 느림

```

```python
# import numpy as np 

def solution(arr):

    # np.mean(arr)

    return sum(arr)/len(arr) # 이게 더 빠르다
```python

<br>

## 하샤드 수

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python
def solution(x):
    arr = list(str(x))
    num = 0

    for i in arr:
        num = num + int(i)

    return True if (x%num) == 0 else False

def main():
    arr = 13
    print(solution(arr))

if __name__ == '__main__':
    main()
```

```python
def solution(x):
    
    sum_x = sum(list(map(int, list(str(x)))))

    if x % sum_x == 0:
        return True
    
    return False
```

<br>

## 핸드폰 번호 가리기

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python
def solution(phone_number):
    answer = list(phone_number)

    for i in range(len(answer)-4):
        answer[i] = "*" 

    return ''.join(answer)
```

```python
def solution(phone_number):
    answer = ''
    
    for i in phone_number[0:-4]:
        answer += i.replace(i, '*')
        
    return answer + phone_number[-4:]
```

> ```python
> ("*" * (len(s) - 4)) + s[-4:]
> ```

<br>

## 행렬의 덧셈

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python
def solution(arr1, arr2):
    answer = [[j for j in range(len(arr1[0]))] for i in range(len(arr1))]

    for i in range(len(arr1)):
        for j in range(len(arr1[i])):
            answer[i][j] = arr1[i][j] + arr2[i][j]

    return answer


def main():
    arr1 = [[1,2], [2,3]]
    arr2 = [[3,4], [5,6]]

    print(solution(arr1, arr2))

if __name__ == '__main__':
    main()
```

```python
def solution(arr1, arr2):
    answer = []

    for i, j in zip(arr1, arr2):
        answer.append(list(map(lambda a,b:a+b, i, j)))
    return answer
```

> ```python
> [list(map(sum, zip(*x))) for x in zip(arr1, arr2)]
> ```

<br>

## 짝수와 홀수

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python
def solution(arr):
    if len(arr)==1:
        answer = [-1]
        return answer

    else:
        arr.remove(min(arr))
        return arr

def main():
    arr = [10]
    print(solution(arr))

if __name__ == '__main__':
    main()
```

<br>

## 최대공약수와 최소공배수

__문제__
두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환하는 함수, solution을 완성해 보세요. 배열의 맨 앞에 최대공약수, 그다음 최소공배수를 넣어 반환하면 됩니다. 예를 들어 두 수 3, 12의 최대공약수는 3, 최소공배수는 12이므로 solution(3, 12)는 [3, 12]를 반환해야 합니다.

__제한사항__

- 두 수는 1이상 1000000이하의 자연수입니다.

__입출력 예__

| n      | m      | return |
| ------ | ------ | ------ |
| 3      | 12     | [3, 12]|
| 2      | 15     | [1, 10]|

__풀이__

```python
import math 

def solution(n, m):
    gcd = math.gcd(n,m)
    
    return [gcd, (n * m) // gcd]
```

<br>

## 정수 제곱근 판별

__문제__

임의의 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하려 합니다.
n이 양의 정수 x의 제곱이라면 x+1의 제곱을 리턴하고, n이 양의 정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하세요.


__제한사항__

- n은 1이상, 50000000000000 이하인 양의 정수입니다.

__입출력 예__

| n      | return |
| ------ | ------ |
| 121    | 144    |
| 3      | -1     |

__풀이__

- int()로 제곱근을 안감싸주니 몇 개의 테스트 케이스에서 오류가 났다 ㅠㅠ 
  
```python
import math

def solution(n):
    if n == int(math.pow(int(math.sqrt(n)), 2)):
        return math.pow(int(math.sqrt(n)) + 1, 2)
                
    else:
        return -1
```

```python
def solution(n):
    if n == int(n ** (0.5)) ** 2:
        return int(n **(0.5) + 1) ** 2
                
    else:
        return -1
```

<br>

## 정수 내림차순으로 배치하기

__문제__
함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

__제한사항__

- n은 1이상 8000000000 이하인 자연수입니다.

__입출력 예__

| n      | return |
| ------ | ------ |
| 118372 | 873211 |

__풀이__

```python
def solution(n):
    s = sorted(str(n), reverse = True)
    return int(''.join(s))
```

<br>


## 자릿수 더하기

__문제__

자연수 N이 주어지면, N의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.
예를들어 N = 123이면 1 + 2 + 3 = 6을 return 하면 됩니다.

__제한사항__

- N의 범위 : 100,000,000 이하의 자연수

__입출력 예__

| N      | answer |
| ------ | ------ |
| 123    | 6      |
| 987    | 24     |

__풀이__

```python
def solution(n):
    return sum(list(map(int, list(str(n)))))
```

> ```python
> sum(map(int, str(number)))
> ```

<br>

## 이상한 문자 만들기

__문제__

문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.


__제한사항__

- 문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
  
- 첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.

__입출력 예__

| s                 | return            |
| ----------------- | ----------------- |
| "try hello world" | "TrY HeLlO WoRlD" |

__풀이__

```python
def solution(s):
    word = list(map(list, s.split(' ')))
    
    for i in range(len(word)):
        for j in range(len(word[i])):
            if j%2 == 0:
                word[i][j] = word[i][j].upper()
                
            elif j%2 == 1:
                word[i][j] = word[i][j].lower()
                
        word[i] = ''.join(word[i])  
    
    return ' '.join(word)
```

> ```python
> return " ".join(map(lambda x: "".join([a.lower() if i % 2 else a.upper() for i, a in enumerate(x)]), s.split(" ")))
> ```

<br>

## 시저 암호

__문제__

어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라고 합니다. 예를 들어 "AB"는 1만큼 밀면 "BC"가 되고, 3만큼 밀면 "DE"가 됩니다. "z"는 1만큼 밀면 "a"가 됩니다. 문자열 s와 거리 n을 입력받아 s를 n만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__
- Z가 넘어가는 경우를 생각해 % 26

```python
def solution(s, n):
    answer = ''
    s = list(s)
    
    for i in range(len(s)): 
        if s[i].isupper(): 
            s[i] = chr((ord(s[i]) - ord('A') + n) % 26 + ord('A')) 
            
        elif s[i].islower(): 
            s[i] = chr((ord(s[i]) - ord('a')+ n) % 26 + ord('a')) 
    
    return "".join(s)
```

<br>

## 소수 찾기

```python
def solution(n):
    answer = 0
    num = set([ i for i in range(2, n+1)])
    
    print(num)
    for i in range(2, n+1):
        num = num - set([i for i in range(i**2, n+1, i)])
    
    return len(num)
```

## 

__문제__

명함 지갑을 만드는 회사에서 지갑의 크기를 정하려고 합니다. 다양한 모양과 크기의 명함들을 모두 수납할 수 있으면서, 작아서 들고 다니기 편한 지갑을 만들어야 합니다. 이러한 요건을 만족하는 지갑을 만들기 위해 디자인팀은 모든 명함의 가로 길이와 세로 길이를 조사했습니다.

아래 표는 4가지 명함의 가로 길이와 세로 길이를 나타냅니다.

| 명함번호 | 가로길이 | 세로길이 |
| ------   | ------   | ------   |
| 1        | 60       | 50       |
| 2        | 30       | 30       |
| 3        | 60       | 30       |
| 4        | 80       | 40       |

가장 긴 가로 길이와 세로 길이가 각각 80, 70이기 때문에 80(가로) x 70(세로) 크기의 지갑을 만들면 모든 명함들을 수납할 수 있습니다. 하지만 2번 명함을 가로로 눕혀 수납한다면 80(가로) x 50(세로) 크기의 지갑으로 모든 명함들을 수납할 수 있습니다. 이때의 지갑 크기는 4000(=80 x 50)입니다.

모든 명함의 가로 길이와 세로 길이를 나타내는 2차원 배열 sizes가 매개변수로 주어집니다. 모든 명함을 수납할 수 있는 가장 작은 지갑을 만들 때, 지갑의 크기를 return 하도록 solution 함수를 완성해주세요.

__제한사항__

- sizes의 길이는 1 이상 10,000 이하입니다.
    - sizes의 원소는 [w, h] 형식입니다.
    - w는 명함의 가로 길이를 나타냅니다.
    - h는 명함의 세로 길이를 나타냅니다.
    - w와 h는 1 이상 1,000 이하인 자연수입니다.

__입출력 예__

| sizes  | result |
| ------ | ------ |
| [[60, 50], [30, 70], [60, 30], [80, 40]]      |	4000 |
| [[10, 7], [12, 3], [8, 15], [14, 7], [5, 15]] |	120  |
| [[14, 4], [19, 6], [6, 16], [18, 7], [7, 11]] |	133  |

__풀이__

```python
def solution(sizes):
    big = [max(e[0],e[1]) for e in sizes]
    small = [min(e[0],e[1]) for e in sizes] 
    
    return max(big) * max(small)
```

>```python
> max(max(x) for x in sizes) * max(min(x) for x in sizes)
>```

<br>


## 비밀지도

__문제__
네오는 평소 프로도가 비상금을 숨겨놓는 장소를 알려줄 비밀지도를 손에 넣었다. 그런데 이 비밀지도는 숫자로 암호화되어 있어 위치를 확인하기 위해서는 암호를 해독해야 한다. 다행히 지도 암호를 해독할 방법을 적어놓은 메모도 함께 발견했다.

지도는 한 변의 길이가 n인 정사각형 배열 형태로, 각 칸은 "공백"(" ") 또는 "벽"("#") 두 종류로 이루어져 있다.
전체 지도는 두 장의 지도를 겹쳐서 얻을 수 있다. 각각 "지도 1"과 "지도 2"라고 하자. 지도 1 또는 지도 2 중 어느 하나라도 벽인 부분은 전체 지도에서도 벽이다. 지도 1과 지도 2에서 모두 공백인 부분은 전체 지도에서도 공백이다.
"지도 1"과 "지도 2"는 각각 정수 배열로 암호화되어 있다.
암호화된 배열은 지도의 각 가로줄에서 벽 부분을 1, 공백 부분을 0으로 부호화했을 때 얻어지는 이진수에 해당하는 값의 배열이다.

네오가 프로도의 비상금을 손에 넣을 수 있도록, 비밀지도의 암호를 해독하는 작업을 도와줄 프로그램을 작성하라.

__제한사항__

- 

__입출력 예__

| n      | return |
| ------ | ------ |
| 12     | 28     |
| 5      | 6      |

__풀이__

```python
def solution(n, arr1, arr2):
    
    answer = []
    b_list = []
    b_list2 = []
    tmp = []
    tmp2 = []
        
    for i in arr1:
        b = []
        for j in range(1, len(arr1)+1):
            b.append(i%2)
            i = i//2
        tmp.append(b)
        
    for i in arr2:
        b = []
        for j in range(1, len(arr2)+1):
            b.append(i%2)
            i = i//2
        tmp2.append(b)
    
    for b in tmp:
        b.reverse()
        b_list.append(b)
    
    for b in tmp2:
        b.reverse()
        b_list2.append(b)

    answer = [[0] * len(b_list) for _ in range(len(b_list))]

    for i in range(len(b_list)):
        for j in range(len(b_list[i])):
            if b_list[i][j] | b_list2[i][j]:
                answer[i][j] = 1 
 
    result = []
    for l in answer:
        for j in range(0, len(l)):
            if l[j] == 1:
                l[j] = '#'
            else:
                l[j] = ' '
        result.append(''.join(l))
    
    return result
```

>```python
>    for i,j in zip(arr1,arr2):
>        a12 = str(bin(i|j)[2:])
>        a12=a12.rjust(n,'0')
>        a12=a12.replace('1','#')
>        a12=a12.replace('0',' ')
>        answer.append(a12)
>```

<br>


## 두 개 뽑아서 더하기 

__문제__

정수 배열 numbers가 주어집니다. numbers에서 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담아 return 하도록 solution 함수를 완성해주세요.

__제한사항__

- numbers의 길이는 2 이상 100 이하입니다.
    - numbers의 모든 수는 0 이상 100 이하입니다.

__입출력 예__

| numbers      | result |
| ------ | ------ |
| [2,1,3,4,1]     | [2,3,4,5,6,7]     |
| [5,0,2,7]      | [2,5,7,9,12]      |

__풀이__

```python
from itertools import combinations

def solution(numbers):
    return sorted(list(set(map(sum, combinations(numbers, 2)))))
```

<br>

## 3진법 뒤집기

__문제__

자연수 n이 매개변수로 주어집니다. n을 3진법 상에서 앞뒤로 뒤집은 후, 이를 다시 10진법으로 표현한 수를 return 하도록 solution 함수를 완성해주세요.

__제한사항__

- n은 1 이상 100,000,000 이하인 자연수입니다.

__입출력 예__

| n      | return |
| ------ | ------ |
| 47     | 7     |
| 125      | 229      |

__풀이__

```python
def solution(n):
    s = ''
    
    while n != 0:
        n, b = divmod(n, 3)
        s += str(b)
        
    return int(s,3)
```

<br>

## 약수의 개수와 덧셈

__문제__

두 정수 left와 right가 매개변수로 주어집니다. left부터 right까지의 모든 수들 중에서, 약수의 개수가 짝수인 수는 더하고, 약수의 개수가 홀수인 수는 뺀 수를 return 하도록 solution 함수를 완성해주세요.

__제한사항__

- 1 ≤ left ≤ right ≤ 1,000

__입출력 예__

| n      | return |
| ------ | ------ |
| 12     | 28     |
| 5      | 6      |

| left | right | result |
| ------ | ------ | ------ |
| 13 | 17 | 43
| 24 | 27 | 52

__풀이__

```python
def solution(left, right):
    answer = []
    e_num = o_num = 0
    n_list = [i for i in range(left, right+1)]
    
    for n in n_list:
        count = 0
        for i in range(1, n):
            if n%i == 0:
                count += 1
                
        if count%2 == 0:
            e_num += n
        else:
            o_num += n
    
    return max(e_num, o_num) - min(e_num, o_num)
```

- 약수가 홀수개인 수는 모두 제곱수

>```python
>    for i in range(left,right+1):
>        if int(i**0.5)==i**0.5:
>            answer -= i
>        else:
>            answer += i
>```

<br>

## 폰켓몬

__문제__

당신은 폰켓몬을 잡기 위한 오랜 여행 끝에, 홍 박사님의 연구실에 도착했습니다. 홍 박사님은 당신에게 자신의 연구실에 있는 총 N 마리의 폰켓몬 중에서 N/2마리를 가져가도 좋다고 했습니다.
홍 박사님 연구실의 폰켓몬은 종류에 따라 번호를 붙여 구분합니다. 따라서 같은 종류의 폰켓몬은 같은 번호를 가지고 있습니다. 예를 들어 연구실에 총 4마리의 폰켓몬이 있고, 각 폰켓몬의 종류 번호가 [3번, 1번, 2번, 3번]이라면 이는 3번 폰켓몬 두 마리, 1번 폰켓몬 한 마리, 2번 폰켓몬 한 마리가 있음을 나타냅니다. 이때, 4마리의 폰켓몬 중 2마리를 고르는 방법은 다음과 같이 6가지가 있습니다.

1. 첫 번째(3번), 두 번째(1번) 폰켓몬을 선택
2. 첫 번째(3번), 세 번째(2번) 폰켓몬을 선택
3. 첫 번째(3번), 네 번째(3번) 폰켓몬을 선택
4. 두 번째(1번), 세 번째(2번) 폰켓몬을 선택
5. 두 번째(1번), 네 번째(3번) 폰켓몬을 선택
6. 세 번째(2번), 네 번째(3번) 폰켓몬을 선택

이때, 첫 번째(3번) 폰켓몬과 네 번째(3번) 폰켓몬을 선택하는 방법은 한 종류(3번 폰켓몬 두 마리)의 폰켓몬만 가질 수 있지만, 다른 방법들은 모두 두 종류의 폰켓몬을 가질 수 있습니다. 따라서 위 예시에서 가질 수 있는 폰켓몬 종류 수의 최댓값은 2가 됩니다.
당신은 최대한 다양한 종류의 폰켓몬을 가지길 원하기 때문에, 최대한 많은 종류의 폰켓몬을 포함해서 N/2마리를 선택하려 합니다. N마리 폰켓몬의 종류 번호가 담긴 배열 nums가 매개변수로 주어질 때, N/2마리의 폰켓몬을 선택하는 방법 중, 가장 많은 종류의 폰켓몬을 선택하는 방법을 찾아, 그때의 폰켓몬 종류 번호의 개수를 return 하도록 solution 함수를 완성해주세요.


__제한사항__

- nums는 폰켓몬의 종류 번호가 담긴 1차원 배열입니다.
- nums의 길이(N)는 1 이상 10,000 이하의 자연수이며, 항상 짝수로 주어집니다.
- 폰켓몬의 종류 번호는 1 이상 200,000 이하의 자연수로 나타냅니다.
- 가장 많은 종류의 폰켓몬을 선택하는 방법이 여러 가지인 경우에도, 선택할 수 있는 폰켓몬 종류 개수의 최댓값 하나만 return 하면 됩니다.

__입출력 예__

| nums      | result |
| ------ | ------ |
| [3,1,2,3]     | 2    |
| [3,3,3,2,2,4] | 3    |
| [3,3,3,2,2,2] |  2   |

nums	result
[3,1,2,3]	2
[3,3,3,2,2,4]	3
[3,3,3,2,2,2]	2

__풀이__

```python
def solution(nums):
    answer = 0
    
    s_num = list(set(nums))
    
    if len(s_num) > len(nums)//2:
        return len(nums)//2
    
    else: 
        return len(s_num)
```

>```python
> min(len(ls)/2, len(set(ls)))
>```

<br>

## 체육복

__문제__

점심시간에 도둑이 들어, 일부 학생이 체육복을 도난당했습니다. 다행히 여벌 체육복이 있는 학생이 이들에게 체육복을 빌려주려 합니다. 학생들의 번호는 체격 순으로 매겨져 있어, 바로 앞번호의 학생이나 바로 뒷번호의 학생에게만 체육복을 빌려줄 수 있습니다. 예를 들어, 4번 학생은 3번 학생이나 5번 학생에게만 체육복을 빌려줄 수 있습니다. 체육복이 없으면 수업을 들을 수 없기 때문에 체육복을 적절히 빌려 최대한 많은 학생이 체육수업을 들어야 합니다.

전체 학생의 수 n, 체육복을 도난당한 학생들의 번호가 담긴 배열 lost, 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열 reserve가 매개변수로 주어질 때, 체육수업을 들을 수 있는 학생의 최댓값을 return 하도록 solution 함수를 작성해주세요.


__제한사항__

- 전체 학생의 수는 2명 이상 30명 이하입니다.
- 체육복을 도난당한 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌의 체육복을 가져온 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌 체육복이 있는 학생만 다른 학생에게 체육복을 빌려줄 수 있습니다.
- 여벌 체육복을 가져온 학생이 체육복을 도난당했을 수 있습니다. 이때 이 학생은 -체육복을 하나만 도난당했다고 가정하며, 남은 체육복이 하나이기에 다른 학생에게는 체육복을 빌려줄 수 없습니다.


__입출력 예__

| n      | return |
| ------ | ------ |
| 12     | 28     |
| 5      | 6      |

| n	| lost	 | reserve | return |
| ------ | ------ | ------ | ------ |
| 5	| [2, 4] |	[1, 3, 5] | 5 |
| 5	| [2, 4] |	[3]	 | 4 |
| 3 | [3]	 | [1]	| 2 |

__풀이__

```python
def solution(n, lost, reserve):
    _reserve = set(reserve) - set(lost)
    _lost = set(lost) - set(reserve)
    
    for r in _reserve:
        f = r - 1
        b = r + 1
        if f in _lost:
            _lost.remove(f)
        elif b in _lost:
            _lost.remove(b)
            
    return n - len(_lost)
```


<br>

## 참고

> [출처: 프로그래머스 코딩 테스트 연습](https://programmers.co.kr/learn/challenges)

<br>


## 

__문제__

__제한사항__

- 

__입출력 예__

| n      | return |
| ------ | ------ |
| 12     | 28     |
| 5      | 6      |

__풀이__

```python

```

>```python
>
>```

<br>