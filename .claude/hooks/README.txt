[hooks 폴더 — 자동 실행 스크립트 보관함]

무엇인가요?
- "언제 ~하면 자동으로 ~해라"를 시키는 스크립트를 두는 곳이에요.
  예) 파일을 고칠 때마다 자동 정리(포맷), 위험한 명령 차단, 작업이 끝나면 알림
- Claude의 기억이나 지시와 다르게, 훅은 프로그램이 직접 실행해요.
  그래서 Claude가 깜빡해도 반드시 실행돼요.

어떻게 쓰나요?
- 주의: Claude Code가 이 폴더를 저절로 읽지는 않아요. 그냥 스크립트를 모아 두는 "관례상 자리"예요.
- 실제 연결은 ../settings.json의 "hooks" 항목에서 해요.

    "hooks": {
      "PostToolUse": [
        {
          "matcher": "Edit|Write",
          "hooks": [
            { "type": "command", "command": "\"$CLAUDE_PROJECT_DIR\"/.claude/hooks/format.sh" }
          ]
        }
      ]
    }

  → 파일을 고치거나 쓴 직후(PostToolUse)에 format.sh를 실행하라는 뜻이에요.
- 자주 쓰는 순간: PreToolUse(도구 쓰기 전), PostToolUse(쓴 후), Stop(답변을 마쳤을 때), SessionStart(대화 시작)
- 스크립트에는 실행 권한이 필요해요: chmod +x 파일이름.sh
