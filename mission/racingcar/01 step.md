# π 1λ¨κ³ λ―Έμ - νμ΅ νμ€νΈ μ€μ΅
# String ν΄λμ€μ λν νμ΅ νμ€νΈ
## μκ΅¬μ¬ν­ 1   
* `1,2`μ ,λ‘ `split()` νμ λ `1`κ³Ό `2`λ‘ μ λΆλ¦¬λλμ§ νμΈνλ νμ΅ νμ€νΈλ₯Ό κ΅¬ννλ€.     
* `1`μ ,λ‘ `split()` νμ λ `1`λ§μ ν¬ν¨νλ λ°°μ΄μ΄ λ°νλλμ§μ λν νμ΅ νμ€νΈλ₯Ό κ΅¬ννλ€.      
        
<details>
<summary>ννΈ</summary>
<div markdown="1">   
<br>  
          
* assertjμ `contains()`λ₯Ό νμ©ν΄ λ°ν κ°μ΄ λ§λμ§ κ²μ¦νλ€.       
* assertjμ `containsExactly()`λ₯Ό νμ©ν΄ λ°ν κ°μ΄ λ§λμ§ κ²μ¦νλ€.        
     
```     
μ λ μ§λ¬ΈμμλΆν° κΆκΈμ¦μ΄ μκΈΈ κ²μλλ€.       
μμ λ§νλ―μ΄, λͺ¨λ  λ¨κ³μμ ννΈλ§ μ κ³΅νμ§ κ°μλ₯Ό μ§ννμ§λ μμ΅λλ€.    
κΆκΈμ¦μ΄ μκ²Όλ€λ©΄ κ΅¬κΈλ§μ ν΅ν΄ μ κ·Όν΄λ³΄μΈμ :)    
```     
  
</div>
</details>
    
## μκ΅¬μ¬ν­ 2      
* `(1,2)` κ°μ΄ μ£Όμ΄μ‘μ λ `String`μ `substring()` λ©μλλ₯Ό νμ©ν΄ `()`μ μ κ±°νκ³  `1,2`λ₯Ό λ°ννλλ‘ κ΅¬ννλ€.

## μκ΅¬μ¬ν­ 3
* "abc" κ°μ΄ μ£Όμ΄μ‘μ λ `String`μ `charAt()` λ©μλλ₯Ό νμ©ν΄ νΉμ  μμΉμ λ¬Έμλ₯Ό κ°μ Έμ€λ νμ΅ νμ€νΈλ₯Ό κ΅¬ννλ€.
* `String`μ `charAt()` λ©μλλ₯Ό νμ©ν΄ νΉμ  μμΉμ λ¬Έμλ₯Ό κ°μ Έμ¬ λ μμΉ κ°μ λ²μ΄λλ©΄    
  `StringIndexOutOfBoundsException`μ΄ λ°μνλ λΆλΆμ λν νμ΅ νμ€νΈλ₯Ό κ΅¬ννλ€.
* JUnitμ `@DisplayName`μ νμ©ν΄ νμ€νΈ λ©μλμ μλλ₯Ό λλ¬λΈλ€.

<details>
<summary>ννΈ</summary>
<div markdown="1">   
<br>  
  
[AssertJ Exception Assertions λ¬Έμ μ°Έκ³ ](https://joel-costigliola.github.io/assertj/assertj-core-features-highlight.html#exception-assertion)   
      
```java
import static org.assertj.core.api.Assertions.*;

assertThatThrownBy(() -> {
    // ...
}).isInstanceOf(IndexOutOfBoundsException.class)
  .hasMessageContaining("Index: 2, Size: 2");
import static org.assertj.core.api.Assertions.assertThatExceptionOfType;

assertThatExceptionOfType(IndexOutOfBoundsException.class)
  .isThrownBy(() -> {
      // ...
}).withMessageMatching("Index: \\d+, Size: \\d+");
```
    
* μμ£Ό λ°μνλ Exceptionμ κ²½μ° Exceptionλ³ λ©μλ μ κ³΅νκ³  μμ
    * assertThatIllegalArgumentException()
    * assertThatIllegalStateException()
    * assertThatIOException()
    * assertThatNullPointerException()
   
</div>
</details>

# Set Collectionμ λν νμ΅ νμ€νΈ
* λ€μκ³Ό κ°μ Set λ°μ΄ν°κ° μ£Όμ΄μ‘μ λ μκ΅¬μ¬ν­μ λ§μ‘±ν΄μΌ νλ€.

```java
public class SetTest {
    private Set<Integer> numbers;

    @BeforeEach
    void setUp() {
        numbers = new HashSet<>();
        numbers.add(1);
        numbers.add(1);
        numbers.add(2);
        numbers.add(3);
    }
    
    // Test Case κ΅¬ν
}
```
    
## μκ΅¬μ¬ν­ 1
* Setμ size() λ©μλλ₯Ό νμ©ν΄ Setμ ν¬κΈ°λ₯Ό νμΈνλ νμ΅νμ€νΈλ₯Ό κ΅¬ννλ€.

## μκ΅¬μ¬ν­ 2
* Setμ contains() λ©μλλ₯Ό νμ©ν΄ 1, 2, 3μ κ°μ΄ μ‘΄μ¬νλμ§λ₯Ό νμΈνλ νμ΅νμ€νΈλ₯Ό κ΅¬ννλ €νλ€.
* κ΅¬ννκ³  λ³΄λ λ€μκ³Ό κ°μ΄ μ€λ³΅ μ½λκ° κ³μν΄μ λ°μνλ€.
* JUnitμ `ParameterizedTest`λ₯Ό νμ©ν΄ μ€λ³΅ μ½λλ₯Ό μ κ±°ν΄ λ³Έλ€.   
   
```java
    @Test
    void contains() {
        assertThat(numbers.contains(1)).isTrue();
        assertThat(numbers.contains(2)).isTrue();
        assertThat(numbers.contains(3)).isTrue();
    }
```      

<details>
<summary>ννΈ</summary>
<div markdown="1">   
<br>  
            
[Guide to JUnit 5 Parameterized Tests](https://www.baeldung.com/parameterized-tests-junit-5)   
   
```java
@ParameterizedTest
@ValueSource(strings = {"", "  "})
void isBlank_ShouldReturnTrueForNullOrBlankStrings(String input) {
    assertTrue(Strings.isBlank(input));
}
```
  
</div>
</details>

## μκ΅¬μ¬ν­ 3
* μκ΅¬μ¬ν­ 2λ contains λ©μλ κ²°κ³Ό κ°μ΄ trueμΈ κ²½μ°λ§ νμ€νΈ κ°λ₯νλ€. 
* μλ ₯ κ°μ λ°λΌ κ²°κ³Ό κ°μ΄ λ€λ₯Έ κ²½μ°μ λν νμ€νΈλ κ°λ₯νλλ‘ κ΅¬ννλ€.
* μλ₯Ό λ€μ΄ 1, 2, 3 κ°μ contains λ©μλ μ€νκ²°κ³Ό true, 4, 5 κ°μ λ£μΌλ©΄ false κ° λ°νλλ νμ€νΈλ₯Ό νλμ Test Caseλ‘ κ΅¬ννλ€.

<details>
<summary>ννΈ</summary>
<div markdown="1">   
<br>  
        
* [Guide to JUnit 5 Parameterized Tests λ¬Έμ](https://www.baeldung.com/parameterized-tests-junit-5)μμ @CsvSourceλ₯Ό νμ©νλ€.
```java
@ParameterizedTest
@CsvSource(value = {"test:test", "tEst:test", "Java:java"}, delimiter = ':')
void toLowerCase_ShouldGenerateTheExpectedLowercaseValue(String input, String expected) {
    String actualValue = input.toLowerCase();
    assertEquals(expected, actualValue);
}
```

</div>
</details>

assertj νμ©   
[Introduction to AssertJ λ¬Έμ](https://www.baeldung.com/introduction-to-assertj)λ₯Ό μ°Έκ³ ν΄ assertjμ λ€μν νμ©λ² μ΅νλ€.
