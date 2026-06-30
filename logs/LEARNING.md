# What is Unit Testing in Java?

## Question
> Explain me about unit test for Java application and why it's important.

---

## What is a Unit Test?

A unit test verifies a single, isolated piece of logic — typically one method or class — in complete isolation from the rest of the system (no database, no network, no file system).

---

## Why It Matters

| Reason | Explanation |
|---|---|
| **Catch bugs early** | Bugs found during development cost ~10x less than bugs found in production |
| **Safe refactoring** | Change internals confidently — if tests still pass, behavior is preserved |
| **Living documentation** | Tests show exactly how code is supposed to behave, with concrete examples |
| **Faster debugging** | A failing unit test points directly at the broken method, not a symptom 3 layers deep |
| **Design pressure** | Hard-to-test code is usually poorly designed — tests force better architecture |

---

## The Standard Java Stack

- **JUnit 5** — the test runner and assertion library (most common)
- **Mockito** — for mocking dependencies so tests stay isolated

### Basic Example

```java
// The class under test
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

```java
// The unit test
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class CalculatorTest {

    @Test
    void add_twoPositiveNumbers_returnsSum() {
        Calculator calc = new Calculator();
        int result = calc.add(3, 4);
        assertEquals(7, result);
    }

    @Test
    void add_negativeAndPositive_returnsCorrectResult() {
        Calculator calc = new Calculator();
        assertEquals(-1, calc.add(-4, 3));
    }
}
```

---

## Testing with Dependencies (Mockito)

When your class depends on something external (a database, a service), you mock it:

```java
// Service under test
public class OrderService {
    private final PaymentGateway gateway;

    public OrderService(PaymentGateway gateway) {
        this.gateway = gateway;
    }

    public boolean placeOrder(double amount) {
        return gateway.charge(amount);
    }
}
```

```java
import org.junit.jupiter.api.Test;
import static org.mockito.Mockito.*;
import static org.junit.jupiter.api.Assertions.*;

class OrderServiceTest {

    @Test
    void placeOrder_whenPaymentSucceeds_returnsTrue() {
        PaymentGateway mockGateway = mock(PaymentGateway.class);
        when(mockGateway.charge(100.0)).thenReturn(true);

        OrderService service = new OrderService(mockGateway);

        assertTrue(service.placeOrder(100.0));
        verify(mockGateway).charge(100.0);
    }
}
```

---

## The AAA Pattern

Every test should follow three steps:

1. **Arrange** — set up the inputs and mocks
2. **Act** — call the method being tested
3. **Assert** — verify the output is correct

---

## What NOT to Unit Test

- Framework code (Spring Boot routing, JPA queries) — that is integration testing
- Pure getters/setters with no logic
- External systems directly — mock them instead

---

## Bottom Line

Unit tests are cheap to write, fast to run, and the primary safety net that lets a team move fast without breaking things. In Java, **JUnit 5 + Mockito** covers 90% of what you need.
