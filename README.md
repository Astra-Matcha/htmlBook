# htmlBook
어디서나 원하는 책 읽고 싶으니깐

1. 책 구조의 기본 단위: .leaf와 .page
.leaf: 종이 한 장을 의미하며, 반드시 앞면(.page.front)과 뒷면(.page.back)을 한 쌍으로 넣어야 합니다.

앞면은 오른쪽 페이지로 보이다가 넘기면 왼쪽으로 회전하고, 뒷면은 회전 후 왼쪽 페이지가 됩니다.

2. 본문과 하단 영역 분리: .content와 .page-footer
.content: 장 제목(<h2>)과 본문 단락(<p>)을 넣는 영역입니다.

.page-footer: 페이지 최하단에 고정되는 영역으로, 각주 목록(.footnotes)과 쪽 번호(.page-num)를 담습니다. 각주가 없는 페이지는 .footnotes를 생략할 수 있습니다.

3. 각주 연결 문법: data-fn과 id 매칭
본문 위첨자: <span class="fn-ref" data-fn="고유ID">번호)</span>

하단 각주 박스: <div class="fn-item" id="고유ID"><strong>번호)</strong> 설명</div>

필수 규칙: data-fn 값과 id 값이 정확히 일치해야 하며, id는 책 전체에서 중복되지 않는 고유한 이름을 써야 합니다.

4. 본문 내 HTML 코드 표기법 (이스케이프)
본문에서 <span ...> 같은 HTML 태그를 실제 태그가 아닌 설명용 텍스트로 보여주려면 특수문자를 치환해야 합니다.

< → &lt;

> → &gt;

" → &quot;

& → &amp;

5. CSS 문법 주의사항
오타 수정: <style> 상단의 - { box-sizing: border-box; }는 전체 선택자인 *** { box-sizing: border-box; }로 수정해야 정상 작동합니다.

분량 조절: 페이지 높이가 고정되어 있으므로, 한 면에 글을 너무 많이 넣으면 하단 각주·쪽 번호와 겹칠 수 있어 페이지별로 적절히 분량을 나누어야 합니다.

표지 구성: .cover 클래스를 함께 지정해 앞표지(.page.front.cover)와 뒷표지(.page.back.cover)를 만듭니다.
