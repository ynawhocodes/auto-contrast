# auto-contrast.js

배경색에 따라 글자 색을 자동으로 **검정** 또는 **흰색**으로 바꿔주는 스크립트입니다.  
`mix-blend-mode: difference` 없이, 항상 읽기 좋은 흑/백 글자색을 적용합니다.

## 사용법

### 1. JS 파일 준비

`auto-contrast.js` 파일을 프로젝트 폴더에 복사합니다.

### 2. HTML에 스크립트 한 줄 추가

`</body>` 바로 위에 아래 한 줄을 넣습니다.

```html
<script src="auto-contrast.js"></script>
```

### 3. 원하는 요소에 클래스 추가

글자색을 자동으로 바꾸고 싶은 요소에 `auto-contrast` 클래스를 넣으면 끝입니다.

```html
<div style="background: #1a1a1a;">
  <p class="auto-contrast">이 글자는 자동으로 흰색이 됩니다</p>
</div>

<div style="background: #f5f5f5;">
  <p class="auto-contrast">이 글자는 자동으로 검정이 됩니다</p>
</div>
```

## 동작 방식

1. `.auto-contrast` 클래스가 붙은 요소를 찾습니다.
2. 해당 요소(또는 부모)의 배경색을 읽습니다.
3. WCAG 상대 휘도 공식으로 밝기를 계산합니다.
4. 밝은 배경 → 검정 글자, 어두운 배경 → 흰색 글자를 적용합니다.

동적으로 추가되는 요소나 스타일 변경도 자동 감지합니다.

## 예시

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <title>auto-contrast 예시</title>
  </head>
  <body>
    <div style="background: #ff6600; padding: 20px;">
      <h1 class="auto-contrast">주황색 배경 위의 텍스트</h1>
    </div>
    <div style="background: #003366; padding: 20px;">
      <h1 class="auto-contrast">남색 배경 위의 텍스트</h1>
    </div>
    <script src="auto-contrast.js"></script>
  </body>
</html>
```
