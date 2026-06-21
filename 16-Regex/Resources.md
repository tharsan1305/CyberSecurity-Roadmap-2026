# Day 16 - Resources

## Tools Used
- Python `re` module
- regex101.com (interactive regex tester with explanation)

## Pattern Quick Reference
| Pattern | Meaning |
|---|---|
| `.` | any character |
| `\d` | digit |
| `\w` | word character |
| `\s` | whitespace |
| `^` / `$` | start / end of string |
| `*` | 0 or more |
| `+` | 1 or more |
| `?` | 0 or 1 |
| `{n,m}` | between n and m occurrences |
| `()` | capturing group |
| `(?=...)` | positive lookahead |
| `(?!...)` | negative lookahead |

## Python re Module Functions
| Function | Purpose |
|---|---|
| `re.search()` | find first match anywhere in string |
| `re.match()` | match only at the start of string |
| `re.findall()` | return all matches as a list |
| `re.sub()` | replace matches with new text |
| `re.IGNORECASE` | flag for case-insensitive matching |

## Further Reading
- regex101.com (test patterns interactively, free)
- Python `re` module official documentation
- OWASP: Regex-based input validation cheat sheet

## Skills Gained Today
- Core regex pattern writing
- Quantifiers, anchors, groups, lookarounds
- Log parsing and IP/status code extraction
- Basic security pattern detection (SQLi signature matching)
- Input validation (email format checking)
