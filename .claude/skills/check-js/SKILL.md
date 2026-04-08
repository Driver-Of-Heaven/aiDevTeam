---
name: check-js
description: Run JS syntax check on HTML files in the ioRisk project after modification. Checks escaped backticks and Node.js syntax validation.
disable-model-invocation: false
allowed-tools: Bash, Read, Glob
---

# JS Syntax Check (ioRisk)

After any HTML file modification in the ioRisk project:

1. Navigate to: `cd projects/ioRisk`
2. Find the target HTML file (default: the main dashboard HTML in 参考DEMO/)
3. Run: `bash check_js.sh <filename>`
4. If errors found:
   - Report the error line number and context
   - Fix the issue (usually nested template literals or escaped backticks)
   - Re-run the check until clean
5. Report: "JS syntax check passed" or details of remaining issues
