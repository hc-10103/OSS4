# Assignment 2-2. HTML Form & CSS

- 학번: 22500819
- 주제: 학생 프로필 등록

이름, 학번, 연락처와 관심 분야를 입력하는 폼을 만들었습니다. 같은 입력 항목을 가진 두 페이지를 만들고, CSS 적용 전후를 비교할 수 있도록 구성했습니다.


## 파일 구성

- [index.html](index.html): 두 실습 페이지로 이동하는 링크
- [form1.html](form1.html): CSS를 적용하지 않은 기본 폼
- [form1_css.html](form1_css.html): 같은 폼에 CSS를 적용한 페이지
- [README.md](README.md): 과제 소개와 Weekly Review


## Weekly Review

### 1. Key Learning

1. **입력 목적에 맞는 Form 요소 사용**
   이름에는 text, 날짜에는 date, 하나만 선택하는 항목에는 radio, 여러 개를 선택하는 항목에는 checkbox를 사용합니다. 선택지를 제공할 때는 select, 여러 줄을 입력받을 때는 textarea를 사용합니다.

2. **입력 요소의 속성 구분**
   id는 요소를 식별하고 label의 for와 연결할 때 사용합니다. name은 폼 데이터의 항목 이름입니다. required는 필수 입력을 지정하고, pattern은 입력 형식을 검사합니다. placeholder는 입력 예시를 보여 주지만 실제 입력값은 아닙니다.

3. **HTML과 CSS의 역할 구분**
   HTML로 입력 항목과 문서 구조를 만들고 CSS로 색상, 여백, 배치를 조정합니다. focus와 hover를 사용하면 입력란을 선택하거나 버튼에 마우스를 올렸을 때의 모습도 바꿀 수 있습니다.

### 2. Form Elements

라디오 버튼과 체크박스의 개별 선택지를 하나씩 세지 않고, 입력 항목 기준으로 총 12개를 구성했습니다.

| 입력 항목 | 사용한 요소 | 용도 |
| --- | --- | --- |
| 이름 | input type="text" | 이름 입력 |
| 학번 | input type="text" | 숫자 8자리 입력 |
| 전화번호 | input type="tel" | 하이픈을 포함한 전화번호 입력 |
| 이메일 | input type="email" | 이메일 형식으로 입력 |
| 생년월일 | input type="date" | 날짜 선택 |
| 전공 | select, option, optgroup | 계열별로 묶인 전공 선택 |
| 학년 | select, option | 학년 선택 |
| 스터디 참여 가능일 | input type="date" | 참여 가능한 날짜 선택 |
| 선호 연락 방법 | input type="radio" | 이메일, 전화, 문자 중 하나 선택 |
| 관심 분야 | input type="checkbox" | 관심 분야 여러 개 선택 |
| 자기소개 | textarea | 여러 줄 입력, 최대 300자 |
| 학습용 폼 확인 | input type="checkbox" | 입력 내용이 저장되지 않는다는 점 확인 |

관련 항목은 fieldset으로 묶고 legend로 제목을 붙였습니다. label은 각 입력 요소의 id와 연결했습니다. 버튼은 입력 확인용 submit과 초기화용 reset을 사용했습니다.

### 3. HTML vs CSS

`form1.html`은 브라우저 기본 스타일을 사용합니다. `form1_css.html`은 같은 폼 구조에 내부 `<style>`로 CSS를 적용했습니다. 

- color와 background-color로 글자색과 배경색을 지정했습니다.
- border와 border-radius로 테두리와 둥근 모서리를 만들었습니다.
- padding은 요소 안쪽 여백, margin은 바깥쪽 여백을 조절하는 데 사용했습니다.
- width로 입력란의 너비를 정하고, Grid와 Flex로 항목을 배치했습니다.
- 기본 정보는 두 열로 배치하고 화면 너비가 560px 이하이면 한 열로 바뀌도록 했습니다.
- focus 상태에서는 입력란의 테두리를 강조하고, hover 상태에서는 버튼 색이 바뀌도록 했습니다.

두 페이지 모두 같은 입력 조건과 JavaScript를 사용하므로 입력 확인과 초기화 동작은 같습니다.

### 4. Problem & Solution

**학번을 숫자 8자리로 제한하는 방법**
학번은 계산하는 숫자가 아닌 식별자이므로 text 타입을 사용했습니다. maxlength="8"로 길이를 제한하고 pattern="[0-9]{8}"로 숫자 8자리인지 검사하도록 했습니다. inputmode="numeric"은 모바일에서 숫자 키보드를 표시하도록 돕는 속성으로 사용했습니다.

**하나만 선택하는 항목과 여러 개 선택하는 항목의 구분**
선호 연락 방법은 radio 버튼들의 name을 contactMethod로 통일했습니다. 관심 분야는 여러 항목을 동시에 고를 수 있도록 checkbox를 사용했습니다.

**학습용 폼의 제출 동작 처리**
입력 형식을 확인한 뒤 실제 제출은 하지 않도록 submit 이벤트에서 preventDefault()를 사용했습니다. 검사에 통과하면 안내 문구를 표시하고, 입력을 수정하거나 초기화하면 이전 문구를 지우도록 했습니다.

### 5. Reflection

이번 코드에서 중요하게 정리한 부분은 태그뿐 아니라 속성에 따라서도 폼의 동작이 달라진다는 점입니다. 같은 input이라도 type에 따라 입력 방식이 달라지고, radio는 같은 name으로 묶어야 하나만 선택할 수 있습니다.

CSS에서는 class 이름만 붙이는 것으로 디자인이 적용되는 것은 아니라는 점을 확인할 수 있습니다. 예를 들어 container라는 이름을 붙였더라도, 그 클래스를 선택하는 CSS에 너비와 여백을 지정해야 가운데 배치됩니다.

앞으로는 입력한 내용을 실제 서버에 전달할 때 GET과 POST가 어떻게 다른지, 서버에서는 입력값을 어떻게 검사하고 저장하는지 더 공부하고 싶습니다.



## 제출 정보

- 최종 제출 GitHub Repository URL: (https://github.com/2026-2-OSS/assign04-c02-22500819)
- 배포 URL: (https://oss-4-orcin.vercel.app/)
- clone coding URL (참고만 하고 자체제작) : https://getbootstrap.com/docs/5.2/examples/checkout/