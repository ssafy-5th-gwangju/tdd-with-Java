# 🚀 1단계 미션 - 학습 테스트 실습
# String 클래스에 대한 학습 테스트
## 요구사항 1   
* `1,2`을 ,로 `split()` 했을 때 `1`과 `2`로 잘 분리되는지 확인하는 학습 테스트를 구현한다.     
* `1`을 ,로 `split()` 했을 때 `1`만을 포함하는 배열이 반환되는지에 대한 학습 테스트를 구현한다.      
        
<details>
<summary>힌트</summary>
<div markdown="1">   
<br>  
          
* assertj의 `contains()`를 활용해 반환 값이 맞는지 검증한다.       
* assertj의 `containsExactly()`를 활용해 반환 값이 맞는지 검증한다.        
     
```     
위 두 지문에서부터 궁금증이 생길 것입니다.       
앞서 말했듯이, 모든 단계에서 힌트만 제공하지 강의를 진행하지는 않습니다.    
궁금증이 생겼다면 구글링을 통해 접근해보세요 :)    
```     
  
</div>
</details>
    
## 요구사항 2      
* `(1,2)` 값이 주어졌을 때 `String`의 `substring()` 메소드를 활용해 `()`을 제거하고 `1,2`를 반환하도록 구현한다.

## 요구사항 3
* "abc" 값이 주어졌을 때 `String`의 `charAt()` 메소드를 활용해 특정 위치의 문자를 가져오는 학습 테스트를 구현한다.
* `String`의 `charAt()` 메소드를 활용해 특정 위치의 문자를 가져올 때 위치 값을 벗어나면    
  `StringIndexOutOfBoundsException`이 발생하는 부분에 대한 학습 테스트를 구현한다.
* JUnit의 `@DisplayName`을 활용해 테스트 메소드의 의도를 드러낸다.

<details>
<summary>힌트</summary>
<div markdown="1">   
<br>  
  
[AssertJ Exception Assertions 문서 참고](https://joel-costigliola.github.io/assertj/assertj-core-features-highlight.html#exception-assertion)   
      
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
    
* 자주 발생하는 Exception의 경우 Exception별 메서드 제공하고 있음
    * assertThatIllegalArgumentException()
    * assertThatIllegalStateException()
    * assertThatIOException()
    * assertThatNullPointerException()
   
</div>
</details>

# Set Collection에 대한 학습 테스트
* 다음과 같은 Set 데이터가 주어졌을 때 요구사항을 만족해야 한다.

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
    
    // Test Case 구현
}
```
    
## 요구사항 1
* Set의 size() 메소드를 활용해 Set의 크기를 확인하는 학습테스트를 구현한다.

## 요구사항 2
* Set의 contains() 메소드를 활용해 1, 2, 3의 값이 존재하는지를 확인하는 학습테스트를 구현하려한다.
* 구현하고 보니 다음과 같이 중복 코드가 계속해서 발생한다.
* JUnit의 `ParameterizedTest`를 활용해 중복 코드를 제거해 본다.   
   
```java
    @Test
    void contains() {
        assertThat(numbers.contains(1)).isTrue();
        assertThat(numbers.contains(2)).isTrue();
        assertThat(numbers.contains(3)).isTrue();
    }
```      

<details>
<summary>힌트</summary>
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

## 요구사항 3
* 요구사항 2는 contains 메소드 결과 값이 true인 경우만 테스트 가능하다. 
* 입력 값에 따라 결과 값이 다른 경우에 대한 테스트도 가능하도록 구현한다.
* 예를 들어 1, 2, 3 값은 contains 메소드 실행결과 true, 4, 5 값을 넣으면 false 가 반환되는 테스트를 하나의 Test Case로 구현한다.

<details>
<summary>힌트</summary>
<div markdown="1">   
<br>  
        
* [Guide to JUnit 5 Parameterized Tests 문서](https://www.baeldung.com/parameterized-tests-junit-5)에서 @CsvSource를 활용한다.
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

assertj 활용   
[Introduction to AssertJ 문서](https://www.baeldung.com/introduction-to-assertj)를 참고해 assertj의 다양한 활용법 익힌다.
