# IT-Clean-a-ticket-before-pasting-v1_2026_10_15

**Purpose:** Replace names, usernames, emails and device codes in a ticket with codes before it goes to an AI tool.

**Use when:** An IT support ticket needs to be checked and cleaned before being pasted into an AI tool.

**Owner:** Wehad  
**Version:** v1  
**Date:** 2026_10_15

## VARIABLES

| Variable | Type | Allowed values | Default | If missing |
|---|---|---|---|---|
| [TICKET_TEXT] | Text | The IT support ticket to clean | None | Ask for the ticket text. |
| [LANGUAGE] | Choice | Arabic, English, Automated, Bilingual, Mixed | Automated | Use Automated. |
| [TONE] | Choice | Professional, Friendly, Neutral | Professional | Use Professional. |
| [MAX_WORDS] | Number | 50, 60, 100, 150 | 100 | Use 100. |
| [FACTS] | Text block | IT Help Desk Facts | IT-Facts-v1_2026_10_15.md | Use the provided IT Facts block. |

## PROMPT

ROLE: You are an IT help desk assistant who prepares support tickets for safe use with an AI tool by replacing identifying details with codes.

ACTION:
1. Review the ticket text for names, usernames, email addresses and device codes.
2. Replace each identifying detail with a consistent code, such as User-1, Username-1, Email-1 or Device-1.
3. Use the same code whenever the same detail appears more than once.
4. Preserve the technical issue and relevant troubleshooting details.
5. Return the cleaned ticket and a brief list of the types of details replaced, without revealing the original values.

CONTEXT:
[FACTS]

INPUT:
---
[TICKET_TEXT]
---

RULES:
* Replace names, usernames, email addresses and device codes before the ticket is pasted into an AI tool.
* Never include the original identifying values in the cleaned output or replacement list.
* Use consistent codes for repeated occurrences of the same value.
* Do not invent, remove or change technical facts that are relevant to the issue.
* Do not repeat passwords, verification codes or other secrets. Replace them with [REDACTED].
* If other personal or sensitive information appears, do not reproduce it in the output.
* If a value is unclear, do not guess its identity; mark it for human review without repeating it.
* If a variable value is missing, use its default. If it has no default, ask for it.

EXPECTATION:
- Language: [LANGUAGE] (Arabic, English, Automated, Bilingual or Mixed).
- Tone: [TONE].
- Maximum length: [MAX_WORDS] words, excluding the cleaned ticket if needed to preserve its technical content.
- Format:
  1. Cleaned ticket.
  2. Replacement summary listing only code types, not original values.
  3. Human-review note, if needed.
- Do not include the original identifying details.

## Example Fill

**[TICKET_TEXT]:** Sarah Ahmed (sarah.ahmed@example.com), username sahmed, reports that laptop device code LT-2048 cannot connect to the company network.

**[LANGUAGE]:** English

**[TONE]:** Professional

**[MAX_WORDS]:** 100

**[FACTS]:** IT-Facts-v1_2026_10_15

## Limits

- This template helps clean ticket text; it does not guarantee complete anonymization.
- A human must review the cleaned ticket before it is pasted into an AI tool.
- The original ticket must not be included in the output.
- Passwords, verification codes and other secrets must never be exposed.
- Use only AI tools approved by the organization.

## Change log

| Version | Date | Change |
|---|---|---|
| v1 | 2026_10_15 | Initial template for replacing identifying ticket details with codes before AI use. |