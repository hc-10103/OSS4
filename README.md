# Assignment 2-2. HTML Form & CSS

- 학번: 22500819
- 주제: 학생 프로필 등록
- 제작 방식: 수업에서 자유주제를 허용하여 클론 코딩 대신 직접 구성했습니다.
- 클론 코딩 원본 URL: 해당 없음 (자유주제)

## 페이지 구성

| 파일 | 내용 |
| --- | --- |
| `index.html` | 기본 HTML / CSS 적용 페이지로 이동하는 홈 |
| `form1.html` | CSS 없이 Form 태그와 입력 요소를 연습하는 페이지 |
| `form1_css.html` | 같은 Form 구조에 CSS를 적용한 페이지 |
| `README.md` | 과제 설명, Weekly Review, Weekly Question |

별도의 설치 없이 `index.html`을 브라우저에서 열면 됩니다.
입력 확인 버튼은 브라우저 유효성 검사를 실행하고 안내 메시지를 표시합니다.
실제 서버 제출, 개인정보 저장, 회원가입 기능은 구현하지 않았습니다. 예시 값으로 테스트합니다.

## Weekly Review

다음 내용은 코드 구현을 바탕으로 정리한 초안입니다. 제출 전 실제 학습 경험에 맞게 확인합니다.

### Key Learning

1. `label`의 `for`와 입력 요소의 `id`를 연결하면 라벨을 눌러 입력란으로 이동하거나 선택할 수 있습니다. `name`은 폼 데이터의 항목 이름을 정합니다.
2. 같은 `name`의 radio는 하나만 선택할 수 있고, checkbox는 각각 독립적으로 선택할 수 있습니다. `required`, `type="email"`, `pattern` 등으로 브라우저 기본 유효성 검사를 사용할 수 있습니다.
3. HTML은 입력 요소와 문서 구조를 정의하고 CSS는 색상, 여백, 크기, 배치 및 focus/hover 상태를 표현합니다. 같은 구조를 유지하면서 CSS 유무에 따른 차이를 비교할 수 있습니다.

### Form Elements

라디오·체크박스 선택지를 각각 세지 않아도 총 **12개 입력 항목**입니다.

| 번호 | 입력 항목 | 요소 / 속성 | 용도 |
| --- | --- | --- | --- |
| 1 | 이름 | `input type="text"` | 이름 입력, 필수 |
| 2 | 학번 | `input type="text"`, `pattern`, `inputmode` | 8자리 숫자 입력, 필수 |
| 3 | 전화번호 | `input type="tel"`, `pattern` | 하이픈을 포함한 전화번호 입력 |
| 4 | 이메일 | `input type="email"` | 이메일 형식 확인, 필수 |
| 5 | 생년월일 | `input type="date"` | 날짜 선택 |
| 6 | 전공 | `select`, `option`, `optgroup` | 계열별 전공 선택, 필수 |
| 7 | 학년 | `select` | 학년 선택, 필수 |
| 8 | 스터디 참여 가능일 | `input type="date"` | 참여 가능 날짜 선택 |
| 9 | 선호 연락 방법 | `input type="radio"` | 이메일·전화·문자 중 하나 선택, 필수 |
| 10 | 관심 분야 | `input type="checkbox"` | 관심 분야 복수 선택 |
| 11 | 자기소개 | `textarea`, `maxlength` | 여러 줄 텍스트 입력, 최대 300자 |
| 12 | 학습용 폼 확인 | `input type="checkbox"` | 저장하지 않는 실습 폼임을 확인, 필수 |

추가로 `form`, `fieldset`, `legend`, `label`, 제출·초기화 `button`을 사용했습니다.
필수 요소인 text, radio, checkbox, date, select, textarea를 모두 포함합니다.

### HTML vs CSS

두 페이지는 같은 Form 구조, 입력 항목, 유효성 검사 및 확인 동작을 사용합니다.

- `form1.html`: 브라우저 기본 스타일로 태그 자체의 구조를 확인합니다.
- `form1_css.html`: 내부 `<style>`에서 폼 카드, 입력란, select, textarea, button, label을 꾸밉니다.
- `color`, `background-color`, `border`, `border-radius`, `padding`, `margin`, `width`, `display`를 사용합니다.
- 기본 정보는 넓은 화면에서 2열, 560px 이하에서 1열로 배치합니다.
- 입력란의 `:focus`, 버튼과 링크의 `:hover`, 키보드 조작을 위한 `:focus-visible`을 표시합니다.

### Problem & Solution

- 기존 생년월일 input 태그의 닫는 `>`와 `name`이 누락되어 있었습니다. 태그를 완성하고 `name="birthday"`를 지정했습니다.
- 학번은 계산할 숫자가 아니라 고정 길이 식별자이므로 text 타입을 유지하고 `pattern="[0-9]{8}"`과 `inputmode="numeric"`을 적용했습니다.
- 연락 방법을 하나만 고르도록 radio의 `name`을 통일하고, 관심 분야는 checkbox로 구성했습니다.
- 학습용 폼에서 개인정보가 URL에 포함되는 기본 제출을 막기 위해 JavaScript의 `preventDefault()`를 사용했습니다. 검사를 통과하면 상태 메시지만 보여 줍니다.
- 작은 화면에서도 읽기 쉽도록 CSS media query로 기본 정보를 1열로 바꿨습니다.

### Reflection

구현을 통해 정리할 수 있는 점은 Form이 입력란을 나열하는 것뿐 아니라 라벨, 그룹, 입력 조건을 함께 설계하는 작업이라는 것입니다. 특히 radio의 name을 공유하는 방식과 label의 for를 연결하는 방식이 서로 다른 목적이라는 점을 구분할 수 있습니다.

추가로 알아볼 질문: 실제 서버로 폼을 제출할 때 GET과 POST는 어떻게 다르며, 브라우저 검사 외에 서버 측 검사도 필요한 이유는 무엇일까요?

## Weekly Question

AI 생성 문제 초안입니다. 제출 전 내용을 확인하고 Google Form에 문제, 정답, 해설을 함께 입력합니다.

### 문제 1 — 객관식

이메일·전화·문자 중 연락 방법을 **하나만** 선택하도록 radio 버튼 3개를 구성하려면 어떻게 해야 할까요?

1. 세 버튼의 `id`를 모두 같게 지정한다.
2. 세 버튼의 `name`을 같게 하고 `id`는 각각 다르게 지정한다.
3. 세 버튼에 `checked`를 모두 지정한다.
4. 세 버튼을 checkbox로 변경한다.

**정답: 2번**

**해설:** 같은 form 안에서 동일한 name을 가진 radio는 한 그룹이 되어 하나만 선택할 수 있습니다. id는 각 요소를 식별하고 label과 연결하므로 서로 다르게 지정합니다.

### 문제 2 — OX

`input`에 `required`를 지정하고 CSS의 `:focus`로 테두리 색을 바꿨다. 이때 필수 입력 여부는 CSS가 결정한다. (O / X)

**정답: X**

**해설:** 필수 입력 여부는 HTML의 required 속성이 결정합니다. CSS의 :focus는 입력 요소에 포커스가 있을 때의 시각적 표현을 담당합니다.

## 제출 및 배포 상태

- 로컬에 등록된 개인 저장소: https://github.com/hc-10103/OSS4
- 로컬에 등록된 수업 저장소: https://github.com/2026-2-OSS/assign04-c02-22500819
- 최종 제출 저장소 및 배포 URL: 확인 필요
- 과제 본문은 Netlify, 제출 항목은 Vercel을 언급하므로 실제 제출에 사용할 서비스를 확인합니다.
- Git commit/push, 배포 확인, LMS 제출 및 Google Form 제출 여부는 별도로 확인해야 합니다.
