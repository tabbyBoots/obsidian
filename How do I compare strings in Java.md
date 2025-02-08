### [[java]] [[string]] [[compare]]

### [strings comparison in Java](https://stackoverflow.com/questions/513832/how-do-i-compare-strings-in-java)

You almost **always** want to use `Objects.equals()`. In the **rare** situation where you **know** you're dealing with [interned](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#intern--) strings, you _can_ use `==`.

`==` tests for reference equality (whether they are the same object).

`.equals()` tests for value equality (whether they contain the same data).

[Objects.equals()](http://docs.oracle.com/javase/7/docs/api/java/util/Objects.html#equals\(java.lang.Object,%20java.lang.Object\)) checks for `null` before calling `.equals()` so you don't have to (available as of JDK7, also available in [Guava](https://github.com/google/guava/wiki/CommonObjectUtilitiesExplained#equals)).

Consequently, if you want to test whether two strings have the same value you will probably want to use `Objects.equals()`.

```java
// These two have the same value
new String("test").equals("test") // --> true 

// ... but they are not the same object
new String("test") == "test" // --> false 

// ... neither are these
new String("test") == new String("test") // --> false 

// ... but these are because literals are interned by 
// the compiler and thus refer to the same object
"test" == "test" // --> true 

// ... string literals are concatenated by the compiler
// and the results are interned.
"test" == "te" + "st" // --> true

// ... but you should really just call Objects.equals()
Objects.equals("test", new String("test")) // --> true
Objects.equals(null, "test") // --> false
Objects.equals(null, null) // --> true
```