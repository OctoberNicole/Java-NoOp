Java - NoOp [![Build Status](https://travis-ci.org/jenzz/Java-NoOp.svg?branch=develop)](https://travis-ci.org/jenzz/Java-NoOp)
===========

This is probably one of the simplest Java annotation processing libraries out there.

It generates [no-op implementations](https://en.wikipedia.org/wiki/NOP) of your interfaces.

Usage
-----
* Simply annotate your interface with `@NoOp` like this:

```java
@NoOp
public interface TestInterface {

    byte aByte();

    short aShort();

    int anInt();

    long aLong();

    float aFloat();

    double aDouble();

    char aChar();

    boolean aBoolean();

    String aString();

    void aVoid();
}
```

* And it will generate the following no-op implementation at compile time:

```java
public class NoOpTestInterface implements TestInterface {

  @Override
  public byte aByte() {
    return (byte) 0;
  }

  @Override
  public short aShort() {
    return (short) 0;
  }

  @Override
  public int anInt() {
    return 0;
  }

  @Override
  public long aLong() {
    return 0L;
  }

  @Override
  public float aFloat() {
    return 0.0F;
  }

  @Override
  public double aDouble() {
    return 0.0D;
  }

  @Override
  public char aChar() {
    return ' ';
  }

  @Override
  public boolean aBoolean() {
    return false;
  }

  @Override
  public String aString() {
    return null;
  }

  @Override
  public void aVoid() {
  }
}
```

The implemented methods return the default data type value as per [Java Data Types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html):

| Data type               | Default value |
|:------------------------|:--------------|
| byte                    | 0             |
| short                   | 0             |
| int                     | 0             |
| long                    | 0L            |
| float                   | 0.0f          |
| double                  | 0.0d          |
| char                    | '\u0000'      |
| String (or any object)  | null          |
| boolean                 | false         |

Download
--------

Gradle (using [apt](https://bitbucket.org/hvisser/android-apt)):

```groovy
def noOpVersion = '1.0.0'
compile "com.jenzz.noop:annotation:$noOpVersion"
apt "com.jenzz.noop:processor:$noOpVersion"
```

Maven (using [maven-compiler-plugin](http://maven.apache.org/plugins/maven-compiler-plugin)):

```xml
<dependency>
    <groupId>com.jenzz.noop</groupId>
    <artifactId>annotation</artifactId>
    <version>1.0.0</version>
</dependency>

<build>
    <pluginManagement>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>2.5.1</version>
                <dependencies>
                    <dependency>
                        <groupId>com.jenzz.noop</groupId>
                        <artifactId>processor</artifactId>
                        <version>1.0.0</version>
                    </dependency>
                </dependencies>
            </plugin>
        </plugins>
    </pluginManagement>
</build>
```

Snapshot versions are available in [Sonatype's SNAPSHOTS repository](https://oss.sonatype.org/content/repositories/snapshots).

License
-------
This project is licensed under the [MIT License](https://raw.githubusercontent.com/jenzz/Java-NoOp/master/LICENSE).
