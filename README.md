# Chromium Canary Submission — Kunjana Panthy (@Kunjana001)

## 1. Loom Walkthrough Video
- Video URL: Pending

## 2. Build Info
- Chromium Branch: main
- Chromium Commit ID: Not yet checked out
- Target Built: Not yet built
- Laptop: macOS, Apple M1, 8 GB RAM

## 3. Architecture Notes

### Feature A — X-Candidate-Canary Header
The Browser process reads the --inject-candidate-id command-line switch. The value must be propagated to the URL loading path so that outgoing HTTP and HTTPS requests receive the X-Candidate-Canary header. Requests should remain unchanged when the switch is absent or empty.

### Feature B — Blink Console Hook
The proposed hook is in Blink's FrameConsole::ReportMessageToClient(). It checks for a Console API warning with the exact message "canary-ping" and logs the candidate acknowledgement.

## 4. AI Agent Workflow
- AI Tool: Claude Code and ChatGPT
- Research: Investigating Blink console handling, command-line switch propagation, and network request interception.
- Status: Both features implemented in candidate_canary.patch (26 added C++ lines across 3 files). Patch application verified against source files from Chromium commit ac92a0298517d7d7e9fe7ab37c8521ff259c87a4 using git apply --check. Compilation and runtime behavior have not yet been verified.
