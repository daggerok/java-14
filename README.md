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
        <arg>--enable-preview-features</arg>
      </compilerArgs>
      <forceJavacCompilerUse>true</forceJavacCompilerUse>
      <parameters>true</parameters>
    </configuration>
  </plugin>
  <!-- mvn test -->
  <plugin>
    <artifactId>maven-surefire-plugin</artifactId>
    <configuration>
      <argLine>--enable-preview-features</argLine>
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
