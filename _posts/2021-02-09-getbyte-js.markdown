---
layout: post
title:  "JavaScript 문자열 byte 크기 구하기"
date:   2021-02-09 16:30:36 +0900
categories: JavaScript Bitwise_operation String Byte
---
### 코드 내 변수
s: 문자열(string) 파라미터   
b: 문자열 바이트(byte) 크기 결과   
c: 함수에서 현재 문자열 인덱스의 유니코드(current unicode)   
※ 비트 시프트 예시   
100>>11 == 100 / 2^11   50>>7 == 50 / 2^7   30<<3 == 30 * 2^3


### EUC-KR 기준(한글 2바이트)
```js
function getByteLength(s) {
    return s.split('').map(s => s.charCodeAt(0)).reduce((prev, c) => (prev + ((c === 10) ? 2 : ((c >> 7) ? 2 : 1))), 0);
}
```

### UTF-8 기준(한글 3바이트) 비트 시프트 연산 사용
```js
function getByteLength(s) {
    for(b = i = 0; c = s.charCodeAt(i++); b += c >> 11 ? 3 : c >> 7 ? 2 : 1);
    return b;
}
```

### 참고 사이트   
https://programmingsummaries.tistory.com/239   
https://jaeheon.kr/123

