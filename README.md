# htmlBook
어디서나 원하는 책 읽고 싶으니깐

# 3D 책장 넘김 + 각주 eBook HTML 문법 정리 (1~5)

## 1. 책 구조의 기본 단위: `.leaf`와 `.page`
- **`.leaf`**: 종이 한 장을 나타내며, 반드시 **앞면(`.page.front`)과 뒷면(`.page.back`)을 한 쌍**으로 구성해야 합니다.
- 앞면(`.front`)은 오른쪽 페이지로 표시되다가 넘기면 왼쪽으로 회전하며, 뒷면(`.back`)은 회전 후 왼쪽 페이지가 됩니다.

## 2. 본문과 하단 영역 분리: `.content`와 `.page-footer`
- **`.content`**: 장 제목(`<h2>`)과 본문 단락(`<p>`) 등 주요 텍스트를 넣는 영역입니다.
- **`.page-footer`**: 페이지 하단에 배치되는 영역으로, 각주 목록(`.footnotes`)과 쪽 번호(`.page-num`)를 포함합니다. 각주가 없는 페이지에서는 `.footnotes`를 생략할 수 있습니다.

## 3. 각주 연결 문법: `data-fn`과 `id` 매칭
- **본문 위첨자**: `<span class="fn-ref" data-fn="고유ID">번호)</span>`
- **하단 각주 박스**: `<div class="fn-item" id="고유ID"><strong>번호)</strong> 설명 내용</div>`
- **작성 규칙**: `data-fn` 값과 `id` 값이 **정확히 일치**해야 하며, `id`는 **문서 전체에서 중복되지 않는 고유한 값**을 사용해야 합니다.

## 4. 본문 내 HTML 코드 표기법 (이스케이프)
- 본문에 `<span ...>` 같은 HTML 태그를 실제 요소가 아닌 **설명용 문자열**로 출력하려면 특수문자를 HTML 엔티티로 치환해야 합니다.
  - `<` → `&lt;`
  - `>` → `&gt;`
  - `"` → `&quot;`
  - `&` → `&amp;`

## 5. CSS 문법 주의사항
- **선택자 오타 수정**: `<style>` 상단의 `- { box-sizing: border-box; }`는 전체 선택자인 **`* { box-sizing: border-box; }`**로 수정해야 합니다.
- **페이지 분량 조절**: 페이지 영역 크기가 제한되어 있으므로, 본문이 지나치게 길면 하단 각주나 쪽 번호와 겹칠 수 있어 한 면당 분량을 조절해야 합니다.
- **표지 스타일 적용**: `.cover` 클래스를 함께 사용해 앞표지(`.page.front.cover`)와 뒷표지(`.page.back.cover`)를 구성합니다.

## 6. no-indent
- ** `<p class="no-indent">` 하면 들여쓰기 없음

- '        <div class="page back cover">
        </div>' 백커버

  '<div class="leaf">
        <div class="page front">
          <div class="content">
            <p></p>
          </div>
          <div class="page-footer">
            <div class="footnotes"></div>
            <div class="page-num">- 2 -</div>
          </div>
        </div>
        <div class="page back">
          <div class="content">
            <p></p>
          </div>
          <div class="page-footer">
            <div class="footnotes"></div>
            <div class="page-num">- 3 -</div>
          </div>
        </div>
      </div>'
  페이지
