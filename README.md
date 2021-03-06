# java-14
Yeah baby!

**prepare**

For now, use IntelliJ IDEA 2020 EAP with jdk 14 installed!

```bash
# sdk ls java
# sdk install java 14.ea.36-open
sdk use java 14.ea.36-open
```

**maven**

```xml
<plugins>
  <!-- mvn comopile -->
  <plugin>
    <artifactId>maven-compiler-plugin</artifactId>
    <configuration>
      <release>14</release>
      <compilerArgs>
        <arg>--enable-preview</arg>
      </compilerArgs>
      <forceJavacCompilerUse>true</forceJavacCompilerUse>
      <parameters>true</parameters>
    </configuration>
  </plugin>
  <!-- mvn test -->
  <plugin>
    <artifactId>maven-surefire-plugin</artifactId>
    <configuration>
      <argLine>--enable-preview</argLine>
    </configuration>
  </plugin>
</plugins>
```

## records

**wrong**

previously we usually used something like lombok to acheive case (scala) or data (kotlin) classes functionality in java:

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
class Person {
  private Long id;
  private String name;
}
```

**correct**

but with java 14 we finally have it out of the box!

```java
record Person(Long id, String name) {}
```

**usage**

```java
var p = new Person(1L, "Max");
var id = p.id();
var name = p.name();
System.out.printf("%s is person with id %d and name %s!%n", p, id, name);
// output: Person[id=1, name=Max] is person with id 1 and name Max!
```

## compact constructor

```java
record Person(Long id, String name) {
  Person {
    Assert.isTrue(this.id > 0, "id must be greater than zero.");
    this.name = this.name.toLowerCase();
  }
}
```

## resources

* [YouTube: [2020 DevDotNext Digital Edition] Project Amber: Recent Java Language Features](https://www.youtube.com/watch?v=3smzW46KEI8)

## other repos
* https://github.com/daggerok/java-examples
