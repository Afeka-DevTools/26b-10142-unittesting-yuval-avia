# Unit Tests for App.java

## Question
> Create unit tests for App.java. Use assert functions in AppTest file. Do 80% coverage.

---

## Overview

`App.java` contains 11 static utility methods. Tests were written in `AppTest.java` using **JUnit 5** with `static org.junit.jupiter.api.Assertions.*` imports. All 45 tests pass with 0 failures.

---

## Methods Tested

| Method | Tests Written | Cases Covered |
|---|---|---|
| `add` | 4 | two positives, positive + negative, both zero, both negative |
| `isPrime` | 3 | below 2 (false), known primes (true), composites (false) |
| `reverse` | 3 | normal string, empty string, single char |
| `factorial` | 3 | zero, positive number, negative (exception) |
| `isPalindrome` | 5 | true word, false word, phrase with punctuation, single char, empty string |
| `fibonacciUpTo` | 4 | n=0, n=1, n=10, negative (exception) |
| `charFrequency` | 3 | repeated chars, empty string, all same char |
| `isAnagram` | 6 | true anagram, false, with spaces, case-insensitive, different lengths, both empty |
| `average` | 5 | normal, single element, empty array (exception), all negatives, mixed positive+negative |
| `filterEvens` | 5 | mixed list, all odd, empty list, all even, negative even numbers |
| `mostCommonWord` | 4 | repeated word, single word, text with punctuation, mixed case |

---

## The AppTest.java File

```java
package org.example;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

import java.util.Arrays;
import java.util.List;
import java.util.Map;

class AppTest {

    // ─── add ────────────────────────────────────────────────────────────────

    @Test
    void add_twoPositives_returnsSum() {
        assertEquals(7, App.add(3, 4));
    }

    @Test
    void add_positiveAndNegative_returnsCorrectSum() {
        assertEquals(-1, App.add(3, -4));
    }

    @Test
    void add_bothZero_returnsZero() {
        assertEquals(0, App.add(0, 0));
    }

    @Test
    void add_bothNegative_returnsNegativeSum() {
        assertEquals(-7, App.add(-3, -4));
    }

    // ─── isPrime ────────────────────────────────────────────────────────────

    @Test
    void isPrime_lessThanTwo_returnsFalse() {
        assertFalse(App.isPrime(1));
        assertFalse(App.isPrime(0));
        assertFalse(App.isPrime(-5));
    }

    @Test
    void isPrime_knownPrimes_returnsTrue() {
        assertTrue(App.isPrime(2));
        assertTrue(App.isPrime(3));
        assertTrue(App.isPrime(7));
        assertTrue(App.isPrime(13));
    }

    @Test
    void isPrime_compositeNumbers_returnsFalse() {
        assertFalse(App.isPrime(4));
        assertFalse(App.isPrime(9));
        assertFalse(App.isPrime(15));
    }

    // ─── reverse ────────────────────────────────────────────────────────────

    @Test
    void reverse_regularString_returnsReversed() {
        assertEquals("olleh", App.reverse("hello"));
    }

    @Test
    void reverse_emptyString_returnsEmpty() {
        assertEquals("", App.reverse(""));
    }

    @Test
    void reverse_singleChar_returnsSameChar() {
        assertEquals("a", App.reverse("a"));
    }

    // ─── factorial ──────────────────────────────────────────────────────────

    @Test
    void factorial_zero_returnsOne() {
        assertEquals(1, App.factorial(0));
    }

    @Test
    void factorial_positiveNumber_returnsCorrectResult() {
        assertEquals(120, App.factorial(5));
        assertEquals(1, App.factorial(1));
        assertEquals(6, App.factorial(3));
    }

    @Test
    void factorial_negativeNumber_throwsIllegalArgumentException() {
        assertThrows(IllegalArgumentException.class, () -> App.factorial(-1));
    }

    // ─── isPalindrome ───────────────────────────────────────────────────────

    @Test
    void isPalindrome_palindromeWord_returnsTrue() {
        assertTrue(App.isPalindrome("racecar"));
        assertTrue(App.isPalindrome("madam"));
    }

    @Test
    void isPalindrome_nonPalindrome_returnsFalse() {
        assertFalse(App.isPalindrome("hello"));
        assertFalse(App.isPalindrome("world"));
    }

    @Test
    void isPalindrome_phraseWithSpacesAndPunctuation_returnsTrue() {
        assertTrue(App.isPalindrome("A man a plan a canal Panama"));
    }

    @Test
    void isPalindrome_singleChar_returnsTrue() {
        assertTrue(App.isPalindrome("a"));
    }

    @Test
    void isPalindrome_emptyString_returnsTrue() {
        assertTrue(App.isPalindrome(""));
    }

    // ─── fibonacciUpTo ──────────────────────────────────────────────────────

    @Test
    void fibonacciUpTo_zero_returnsListWithZero() {
        assertEquals(List.of(0), App.fibonacciUpTo(0));
    }

    @Test
    void fibonacciUpTo_ten_returnsCorrectSequence() {
        assertEquals(List.of(0, 1, 1, 2, 3, 5, 8), App.fibonacciUpTo(10));
    }

    @Test
    void fibonacciUpTo_one_returnsTwoElements() {
        assertEquals(List.of(0, 1, 1), App.fibonacciUpTo(1));
    }

    @Test
    void fibonacciUpTo_negative_throwsIllegalArgumentException() {
        assertThrows(IllegalArgumentException.class, () -> App.fibonacciUpTo(-1));
    }

    // ─── charFrequency ──────────────────────────────────────────────────────

    @Test
    void charFrequency_repeatedChars_returnsCorrectCounts() {
        Map<Character, Integer> freq = App.charFrequency("aab");
        assertEquals(2, freq.get('a'));
        assertEquals(1, freq.get('b'));
    }

    @Test
    void charFrequency_emptyString_returnsEmptyMap() {
        assertTrue(App.charFrequency("").isEmpty());
    }

    @Test
    void charFrequency_allSameChar_returnsSingleEntry() {
        Map<Character, Integer> freq = App.charFrequency("aaa");
        assertEquals(1, freq.size());
        assertEquals(3, freq.get('a'));
    }

    // ─── isAnagram ──────────────────────────────────────────────────────────

    @Test
    void isAnagram_trueAnagram_returnsTrue() {
        assertTrue(App.isAnagram("listen", "silent"));
    }

    @Test
    void isAnagram_notAnagram_returnsFalse() {
        assertFalse(App.isAnagram("hello", "world"));
    }

    @Test
    void isAnagram_withSpaces_returnsTrue() {
        assertTrue(App.isAnagram("anagram", "nag a ram"));
    }

    @Test
    void isAnagram_differentCase_returnsTrue() {
        assertTrue(App.isAnagram("Listen", "Silent"));
    }

    @Test
    void isAnagram_differentLengths_returnsFalse() {
        assertFalse(App.isAnagram("cat", "cats"));
    }

    @Test
    void isAnagram_emptyStrings_returnsTrue() {
        assertTrue(App.isAnagram("", ""));
    }

    // ─── average ────────────────────────────────────────────────────────────

    @Test
    void average_normalArray_returnsCorrectAverage() {
        assertEquals(2.0, App.average(new int[]{1, 2, 3}));
    }

    @Test
    void average_singleElement_returnsThatElement() {
        assertEquals(5.0, App.average(new int[]{5}));
    }

    @Test
    void average_emptyArray_throwsIllegalArgumentException() {
        assertThrows(IllegalArgumentException.class, () -> App.average(new int[]{}));
    }

    @Test
    void average_negativeNumbers_returnsCorrectAverage() {
        assertEquals(-2.0, App.average(new int[]{-1, -2, -3}));
    }

    @Test
    void average_mixedPositiveAndNegative_returnsZero() {
        assertEquals(0.0, App.average(new int[]{-5, 5}));
    }

    // ─── filterEvens ────────────────────────────────────────────────────────

    @Test
    void filterEvens_mixedList_returnsOnlyEvens() {
        List<Integer> result = App.filterEvens(Arrays.asList(1, 2, 3, 4, 5));
        assertEquals(List.of(2, 4), result);
    }

    @Test
    void filterEvens_allOdd_returnsEmptyList() {
        List<Integer> result = App.filterEvens(Arrays.asList(1, 3, 5));
        assertTrue(result.isEmpty());
    }

    @Test
    void filterEvens_emptyList_returnsEmptyList() {
        assertTrue(App.filterEvens(List.of()).isEmpty());
    }

    @Test
    void filterEvens_allEven_returnsAllElements() {
        List<Integer> result = App.filterEvens(Arrays.asList(2, 4, 6));
        assertEquals(List.of(2, 4, 6), result);
    }

    @Test
    void filterEvens_negativeEvenNumbers_areIncluded() {
        List<Integer> result = App.filterEvens(Arrays.asList(-4, -3, 2));
        assertEquals(List.of(-4, 2), result);
    }

    // ─── mostCommonWord ─────────────────────────────────────────────────────

    @Test
    void mostCommonWord_repeatedWord_returnsThatWord() {
        assertEquals("the", App.mostCommonWord("the cat and the dog and the bird"));
    }

    @Test
    void mostCommonWord_singleWord_returnsThatWord() {
        assertEquals("hello", App.mostCommonWord("hello"));
    }

    @Test
    void mostCommonWord_textWithPunctuation_returnsCorrectWord() {
        assertEquals("hello", App.mostCommonWord("hello, hello! world."));
    }

    @Test
    void mostCommonWord_mixedCase_returnsLowercase() {
        assertEquals("hello", App.mostCommonWord("Hello hello HELLO world"));
    }
}
```

---

## Assert Functions Used

| Assert | Purpose |
|---|---|
| `assertEquals(expected, actual)` | Verifies a method returns the exact expected value |
| `assertTrue(condition)` | Verifies a boolean result is `true` |
| `assertFalse(condition)` | Verifies a boolean result is `false` |
| `assertThrows(Exception.class, lambda)` | Verifies a method throws the expected exception |

---

## Results

- **45 tests** — 0 failures, 0 errors, 0 skipped
- **Coverage** — all 11 methods covered, all edge cases and code paths verified
- **Coverage enforced** by JaCoCo with `minimum = 0.80` in `build.gradle.kts`
