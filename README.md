# QA Tester Assistant

An AI agent that helps a manual tester turn requirements into risk assessments, test scenarios, step-by-step test cases and ready-to-execute test scripts. The tester reviews and owns all output.

## What it produces

| Deliverable | Description |
|---|---|
| Risk assessment | Risks rated by likelihood and impact, with a suggested testing order |
| Test scenarios | Normal use, edge cases and failure cases |
| Manual test cases | Preconditions, test data, steps and exact expected results |
| Test script | Test cases filled into the Word template (`templates/test-script-template.docx`) |
| Questions and assumptions | Gaps in the requirements listed as questions, never guessed |
| Supporting items | Test data, checklists, bug report drafts (on request) |

## Repository layout

```
qa-tester-assistant/
├── AGENTS.md                              Agent instructions (portable, paste into any assistant)
├── .claude/agents/qa-tester-assistant.md  Same instructions as a Claude Code subagent
├── templates/
│   └── test-script-template.docx          Test script template (Instructions | Expected | Actual)
└── examples/
    └── login-feature/
        ├── requirements.md                Original requirements and the answers to clarifying questions
        ├── qa-deliverables.md             Risks, scenarios, test cases, traceability
        └── Login_Test_Script.docx         Finished test script built from the template
```

## How to use it

**Claude Code**
1. Copy the `.claude/agents/` folder into your project (or into `~/.claude/agents/` to use it everywhere).
2. Ask: `Use the qa-tester-assistant agent to assess risks and write test cases for this requirement: ...`

**Claude Projects, ChatGPT or any other assistant**
1. Paste the contents of `AGENTS.md` into the project instructions or system prompt.
2. Upload `templates/test-script-template.docx` if you want test scripts in that format.
3. Paste your requirements and ask for the deliverable you need.

## Suggested workflow

1. Give the agent your requirements or user story.
2. Review the **questions and assumptions** it returns and answer them.
3. The agent updates the risks and test cases with your answers and flags new questions.
4. Review the test cases, then ask for the test script in the template.
5. Execute the script, filling in the Actual results column.

## Test script format

Each test case is a three-column table. The Actual results column repeats the expected text with blanks, so the tester only fills in the difference:

| Instructions | Expected results | Actual results |
|---|---|---|
| User login as `<U1>` | User is logged in to test environment. | User __ logged in to test environment. |

Creating the `.docx` needs an environment that can write Word files (for example Claude with file creation enabled). Otherwise the agent produces the same table in Markdown.

## Example

`examples/login-feature/` shows the whole flow for a login feature: requirements, clarifying questions and answers, risk assessment, 19 test cases, and the finished test script.

## Customizing

- Edit `AGENTS.md` and `.claude/agents/qa-tester-assistant.md` together so they stay in sync.
- Replace `templates/test-script-template.docx` with your own template and update the "Test script template" section of the instructions to match its columns.

## Notes

- Output is AI-generated and must be reviewed by a tester before use.
