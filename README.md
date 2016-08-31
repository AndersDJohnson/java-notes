# Java notes

## Misc
```java
/* Reflection toString for logging, etc. */
@Override
public String toString() {
  /*
   * Generate toString including transient and static attributes.
   */
  return ReflectionToStringBuilder.toString(this, ToStringStyle.SIMPLE_STYLE, true, true);
}
```

## Stack Traces
```java
Throwable t;
t.getStackTrace();
e.printStackTrace();
```
```java
Thread.currentThread().getStackTrace();
```
```java
String fullStackTrace = org.apache.commons.lang.exception.ExceptionUtils.getFullStackTrace(e);
```

## Reader to String
```java
import org.apache.commons.io.IOUtils;
import org.apache.commons.io.input.ReaderInputStream;

IOUtils.toString(new ReaderInputStream(reader), "UTF-8");
```

## Enum find value

This is a safe alternative to `Enum#valueOf(String string)`.

```java
public enum MyEnum {
  ONE("one"),
  TWO("two");
  
  private String string;

  private MyEnum(String string) {
    this.string = string;
  }

  public static MyEnum find(String string) {
      for (MyEnum value : MyEnum.values()) {
          if (value.string.equalsIgnoreCase(string)) {
              return value;
          }
      }
      return null;
  }
}
```
