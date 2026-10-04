[agents 폴더 — 서브에이전트(전문 도우미)]

무엇인가요?
- 한 가지 일만 맡는 "전문 직원"을 정의하는 곳이에요.
  예) 코드 리뷰어, 테스트 작성자, 버그 추적자
- 도우미는 자기만의 대화창에서 따로 일하고 결과만 보고해요.
  그래서 본 대화가 지저분해지지 않아요.

어떻게 쓰나요?
- .md 파일 하나 = 도우미 한 명이에요. (예: code-reviewer.md)
- 파일 맨 위에 이름표(frontmatter)를 붙여요.

    ---
    name: code-reviewer
    description: 코드를 고친 뒤 버그와 실수를 찾아야 할 때 사용
    tools: Read, Grep, Glob
    model: sonnet
    ---
    (여기부터 도우미에게 주는 업무 지시문)

- description이 제일 중요해요. Claude가 이 문장을 보고 "이 일은 저 도우미에게 맡기자"를 정해요.
- tools를 빼면 모든 도구를 쓸 수 있어요. 줄이면 그만큼 안전해져요.
- Claude Code 안에서 `/agents`를 치면 메뉴로 만들고 고칠 수 있어요.
