        
🐳 공식문서 : https://datatracker.ietf.org/doc/html/rfc8259         
### 📌 개요        
1️⃣ JSON (JavaScript Object Notation)은 이름 그대로 자바스크립트의 객체 타입(Object literals)에서 파생되었고,        
특정 프로그래밍 언어에 종속되지 않는, 구조화된 데이터를 직렬화 하기 위한 텍스트 기반의 표현 방식 이다.        
2️⃣ JSON은 간단한 문법이 있으며, 이를 통해 구조화된 데이터를 유연하게 표현할수 있다.        
3️⃣ JSON 은 4개의 원시타입과 2가지 구조화 타입을 표현할수 있다.        
👉 원시타입 : 문자열(Strings), 실수형(Numbers), 불리언(Booleans), 널(null)        
👉 구조화타입 : 객체(Objects), 배열(Arrays)        
        
### 📌 JSON-Text 정의        
1️⃣ JSON-Text는 토큰이라 불리는 6개의 구조표현문자(Structural characters), 문자열(Strings), 숫자(Numbers), false, null, true 로 구성된다.         
👉 Structural character - '[', ']', '{', '}', ',', ';'        
2️⃣ JSON-Text는 값으로 정의된다.         
```SQL        
JSON-text = ws value ws        
```        
👉 이전 JSON 사양 에서는 JSON-TEXT 의 정의를 객체(Object), 또는 배열(Array) 로 만 정의 되었지만 현재의 정의가 포함 하므로 통용 가능하다.        
        
### 📌 JSON의 Value        
1️⃣ JSON 의 값(Value)은 오직 객체(Object), 배열(Array), 문자열(String), 실수형(Number)과 3가지 literal(false, true, null)만 가능하다.        
👉 true, false, null 3가지 리터럴은 오직 소문자만 가능하다.        
👉 따라서 JSON-text는 아래와 같은 형태이다.        
```SQL        
1. 객체          
    {"name":"홍길동","age":30}        
2. 배열          
    [1, 2, 3, 4]        
3. 문자열          
    "Hello, World!"        
4. 숫자          
    123.45        
5. 불리언          
    true        
6. 널          
    null        
```        
        
### 📌JSON Value - Objects        
1️⃣ Object 는 중괄호({ }) 안에 이름(name)과 값(value)(또는 members)의 쌍으로 구성된다.         
2️⃣ 이떄, 이름과 값의 쌍이 없는 빈 중괄호 {} 역시 Json Object로 정의한다.        
```SQL         
object = begin-object [ member *( value-separator member ) ]          
         end-object          
          
member = string name-separator value        
```        
        
👉이름(name)과 값(value)(또는 members)의 쌍(pair)        
➡️ 이름(name)         
-> 이름은 String 타입이고 해당 Json Object 내에서 Unique 한것이 권장된다.         
-> 이름 뒤에 ':' 이 붙어 값과 구별한다.          
-> 값 뒤에 ','를 통해 다음의 이름값쌍을 구별한다.        
👉 일부 Json 구현체에 대한 Report        
➡️ 중복된 이름 -> 에러를 발생하는 구현체도 있고, 마지막 이름/값 쌍을 바라보는 구현체도 있다.         
        
### 📌JSON Value - Array        
1️⃣ Array는 대괄호([]) 안에 콤마(,)로 구분되는 값(value)(또는 elements)으로 구성된다.        
2️⃣ 마찬가지로 값이 없는 빈 대괄호 [] 역시 JSON Array로 정의된다.        
3️⃣ Array를 구성하는 값들은 서로 다른 타입이어도 무방하다.        
```SQL        
array = begin-array [ value *( value-separator value ) ] end-array        
        
예시        
[        
    {        
        "id": "ID000001",        
        "usable": false,        
	    "qty": 0        
	},        
	1,        
	2,        
	3         
]        
```        
        
### 📌JSON Value - Numbers        
1️⃣ 대부분 프로그래밍 언어와 유사하게 10진법을 사용하며 부호,지수,분수,소수 등의 수를 표현한다.        
2️⃣ 숫자의 범위와 정밀도는 JSON을 구현한 구현체의 범위에 따른다.        
3️⃣ 숫자 값 표현 문법은 아래와 같다.        
```NOTE        
number = [ minus ] int [ frac  ] [  exp  ]          
decimal-point = %x2E ; .          
digit1-9 = %x31-39 ; 1-9          
e = %x65 / %x45 ; e E          
exp = e [ minus / plus ] 1*DIGIT          
frac = decimal-point 1*DIGIT          
int = zero / ( digit1-9 *DIGIT )          
minus = %x2D ; -          
plus = %x2B ; +          
zero = %x30 ; 0        
```        
        
### 📌 JSON Value - Strings        
1️⃣ 스트링은 따움표(" ") 안에 문자열로 정의한다.        
2️⃣ 역슬레쉬, 제어문자 등을 제외하고 모든 유니코드 문자는 따움표 안에 배치하여 문자열로 표현할수 있다.        
3️⃣ 이스케이프 문자열을 스트링으로 표현하기 위해선 역슬레쉬를 이용하여 표현한다. 또한 역슬레쉬와 유니코드 값을 이용하여 모든 문자를 이스케이프 처리할수 있다.        
👉 " -> ' \" '         
4️⃣ JSON-TEXT 의 기본 인코딩은 UTF-8 이며 UTF-16, UTF-32 인코딩도 가능하지만 상호 운영관점에서 실패되는 구현이 많다.        
```NOTE        
string = quotation-mark *char quotation-mark          
          
char = unescaped /          
		escape (          
					%x22 / ; " quotation mark U+0022          
					%x5C / ; \ reverse solidus U+005C          
					%x2F / ; / solidus U+002F          
					%x62 / ; b backspace U+0008          
					%x66 / ; f form feed U+000C          
					%x6E / ; n line feed U+000A          
					%x72 / ; r carriage return U+000D          
					%x74 / ; t tab U+0009          
					%x75 4HEXDIG         
		) ; uXXXX U+XXXX          
          
escape = %x5C ; \          
          
quotation-mark = %x22 ; "          
          
unescaped = %x20-21 / %x23-5B / %x5D-10FFFF        
        
        
// 문자열과 이스케이프 문자표현 예시                      
SELECT '{"quote":"\""}'::json         
                             
SELECT ('{"quote":"\""}'::json ->> 'quote')  ;        
        
SELECT ('{"quote":"\u005C"}'::json ->> 'quote') ;                   
        
select '{"quote":"\u005C"}'::json         
        
SELECT ('{"quote":"\uD834\uDD1E"}'::json ->> 'quote') AS only_quote;        
```        
        
        
        
