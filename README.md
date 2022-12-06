# Advanced-Encryption-Standard-Algorithm

## 문제
키의 길이가 128 비트인 AES (Advanced Encryption Standard) 알고리즘을 FIPS-197 문서에 명시된  
표준스펙에 따라 구현한다.
## 정수형 타입
프로그램에 사용하는 모든 정수형 타입은 uint8_t, int16_t와 같이 부호의 유무와 비트의 크기를  
명확하게 알 수 있도록 C언어 표준 정수형 타입을 사용한다.
## 전역 함수
외부에서 보이는 전역 함수를 아래 열거한 프로토타입을 사용하여 구현한다. 각 함수에 대한 요구사항은  
다음과 같다.
• void KeyExpansion(const uint8_t *key, uint32_t *roundKey) – 길이가 16 바이트인 사  
용자 키에서 암복호에 사용할 라운드 키를 생성한다. roundKey의 길이는 44 워드이어야 한다.  
• void Cipher(uint8_t *state, const uint32_t *roundKey, int mode) – 크기가 16 바이  
트인 state를 roundKey를 사용하여 암복호화한다. 이 때 mode가 ENCRYPT이면 암호화를 수행하고  
DECRYPT이면 복호화를 수행한다.  
## 지역 함수
내부에서만 사용하는 지역 함수는 별도로 지정하지 않고, 각자 필요에 맞게 작성한다. 다음에 열거한  
함수와 프로토타입은 참고용이다.  
• static void AddRoundKey(uint8_t *state, const uint32_t *roundKey) – 라운드 키를  
XOR 연산을 사용하여 state에 더한다.  
• static void SubBytes(uint8_t *state, int mode) – mode에 따라 순방향 또는 역방향으로  
바이트를 치환한다.  
• static void ShiftRows(uint8_t *state, int mode) – mode에 따라 순방향 또는 역방향으  
로 바이트의 위치를 변경한다.  
• static void MixColumns(uint8_t *state, int mode) – 기약 다항식 𝑥^8 + 𝑥^4 + 𝑥^3 + 𝑥 + 1을  
사용한 GF(2^8)에서 행렬곱셈을 수행한다. mode가 DECRYPT이면 역행렬을 곱한다.
