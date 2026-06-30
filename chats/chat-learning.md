# Chat Log – Learning About Unit Testing
**Tool:** Claude Code (Anthropic)
**Part:** 2 — Self-learning with LLM

---

## Conversation

**User:**
> explain me about unitest for java applicatin and why its important

**Claude Code:**

A unit test verifies a single, isolated piece of logic — typically one method or class — in complete isolation from the rest of the system (no database, no network, no file system).

**Why It Matters:**

| Reason | Explanation |
|---|---|
| Catch bugs early | Bugs found during development cost ~10x less than bugs found in production |
| Safe refactoring | Change internals confidently — if tests still pass, behavior is preserved |
| Living documentation | Tests show exactly how code is supposed to behave, with concrete examples |
| Faster debugging | A failing unit test points directly at the broken method |
| Design pressure | Hard-to-test code is usually poorly designed — tests force better architecture |

**The Standard Java Stack:**
- **JUnit 5** — the test runner and assertion library
- **Mockito** — for mocking dependencies so tests stay isolated

**The AAA Pattern every test follows:**
1. **Arrange** — set up inputs and mocks
2. **Act** — call the method being tested
3. **Assert** — verify the output is correct

**Basic example:**
```java
@Test
void add_twoPositiveNumbers_returnsSum() {
    Calculator calc = new Calculator();
    assertEquals(7, calc.add(3, 4));
}
```
