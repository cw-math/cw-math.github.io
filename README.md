# 중학 수학 프로젝트 Github (cw-math.github.io)

## 소수(Prime Number)
- [에라토스테네스의 체로 소수 찾기: Find Prime Numbers using Eratosthenes' sieve](https://cw-math.github.io/PrimeNumber/)

### 소수(Prime Number) 에 대해
 자연수 중에서 다른 자연수를 곱해서 만들수 있는 수들을 "합성수(composite number/compound number)"라고 부른다.
 - 6 = 2x3 = 1x6
 - 12 = 2x2x3 = 2x6 = 4x3 = 1x12

 이렇게 합성수를 만드는 데 쓰이는 수를 "인수/약수"라고 부르고 1과 자기자신도 약수로 포함시킨다. 따라서 12의 약수는 (1,2,3,4,6,12) 6개이다. 
 
 그리고 자연수 중에는 (1,2,3,5,7,11...) 처럼 약수가 1과 자신뿐인 수들이 있다. 
 이중 1을 제외한 수들 (2,3,5,7,11,...) 의 곱으로 모든 합성수를 만들어낼 수 있으므로, (2,3,5,7,11,...) 을 합성수를 만드는 기본 요소라고 볼 수 있다.
 
 이렇게 "약수가 1과 자신뿐인 수로서 1이 아닌 수" 들을 가리켜 수학에서는 소수(Prime Number)라고 부른다.
      

### [에라토스테네스의 체(Eratosthenes' sieve) 로 소수 찾기](https://cw-math.github.io/PrimeNumber/) 
```

소수는 모든 자연수의 배수를 차례로 제거함으로써 찾아낼 수 있다. 
이 방법은 처음 고안한 그리스의 수학자 에라토스테네스(BC273?~192?)의 이름을 따서 '에라토스테네스의 체'라 부른다. 
'체'는 그물구조로 알갱이를 골라내는 도구인데, 2이상의 자연수에서 '2의 배수를 걸러내는 체', '3의 배수를 걸러내는 체', 
'5의 배수를 걸러내는 체' 등이 계속 겹쳐진 체들이 있고, 소수는 이 모든 체를 통과하고 남은 수라고 말할 수 있다. 
```
![eratosthenes](https://user-images.githubusercontent.com/89570304/130923855-1f68fc40-74b6-4fc7-a3f8-d4a0ff778e56.png)

### p5.js 프로그램 설명
```
예를 들어 2~100까지의 자연수를 나타내는 배열 n을 일단 모두 true 로 초기화 한다.

 let n = [];
 for (let i = 2; i <= 100; i++) {
    n[i] = true;
  }

특정 수 a의 배수를 걸러내는 체 함수(sieve) 는 배열 n에서 해당 수의 배수는 모두 false로 셋팅해서 걸러낸다. 
예를 들어 100 이하의 2의 배수를 모두 걸러내는 체:  sieve(2, 100)
        100 이하의 3의 배수를 모두 걸러내는 체:  sieve(3, 100)

function sieve(a,lastN) {
  for (let i = 2; i <= lastN / 2; i++) {
    if (a * i <= lastN) n[a * i] = false;
  }
}

다음과 같이 findPrime(100) 을 호출하여 2~100까지의 체 함수로 거른 이후 자연수 n배열안에 아직 true 인 수들이 소수란다. 

function findPrime(lastN){
  // perform eratosthenes' sieve
  for( let i =2; i <= lastN/2 ; i++){
    sieve(i,lastN);
  }
}
```
