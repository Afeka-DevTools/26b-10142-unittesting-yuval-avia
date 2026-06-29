# Chat Log – Writing Unit Tests for App.java
**Tool:** Claude Code (Anthropic)
**Part:** 3 — Writing unit tests with IDE-integrated LLM

---

## Conversation

---

**User:**
> ok , now create unittest for app.java
> your unitest need to to use assert func in apptest file
> do 80 % coverage

**Claude Code:**

Read `App.java` and identified 11 static utility methods. Wrote 45 unit tests in `AppTest.java` using JUnit 5 with `static org.junit.jupiter.api.Assertions.*`, covering all code paths and edge cases.

Assert functions used:
- `assertEquals` — verifies exact return value
- `assertTrue` — verifies boolean is true
- `assertFalse` — verifies boolean is false
- `assertThrows` — verifies an exception is thrown

Edge cases covered per method:

| Method | Tests | Cases |
|---|---|---|
| `add` | 4 | positives, negative, zero, both negative |
| `isPrime` | 3 | below 2, known primes, composites |
| `reverse` | 3 | normal, empty string, single char |
| `factorial` | 3 | zero, positive, negative (exception) |
| `isPalindrome` | 5 | true, false, punctuation, single char, empty string |
| `fibonacciUpTo` | 4 | n=0, n=1, n=10, negative (exception) |
| `charFrequency` | 3 | repeated chars, empty string, all same |
| `isAnagram` | 6 | true, false, spaces, case, different lengths, both empty |
| `average` | 5 | normal, single, empty (exception), negatives, mixed |
| `filterEvens` | 5 | mixed, all odd, empty, all even, negative evens |
| `mostCommonWord` | 4 | repeated, single, punctuation, mixed case |

All 45 tests passed. BUILD SUCCESSFUL. Coverage above 80% enforced by JaCoCo.
