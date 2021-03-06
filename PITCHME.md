# What is JUnit 5?

---
 
#### JUnit 5 = JUnit Platform + ...

- Foundation for launching testing frameworks |
- Defines and uses `TestEngine` interface     |

+++
 
#### JUnit 5 = ... JUnit Jupiter + ...

- New programming model for writing tests    |
- New extension model for writing extensions |
- `JupiterTestEngine implements TestEngine`  |

+++
 
#### JUnit 5 = ... JUnit Vintage + ...

- Enables running JUnit 3 and JUnit 4 tests |
- `VintageTestEngine implements TestEngine` |

+++

#### JUnit 5 = ... + Your Testing Framework

- What is a test? You define it!          |
- How is a test evaluated? You define it! |
- `YourTestEngine implements TestEngine`  |
- Get tooling support for granted.        |

---

# This is JUnit 5

// big picture from PDF

// now into the red box "Jupiter"

+++

#### Jupiter

- First Jupiter Test
- Annotations |
- Standard Test Class |
- Display Names |
- Assertions |
- Assumptions |
- Disabling Tests |
- Conditional Test Execution |
- Tagging and Filtering |

+++

#### Jupiter

- Test Instance Lifecycle
- Nested Tests |
- Dependency Injection |
- Test Interfaces |
- Repeated Tests |
- Parameterized Tests |
- Test Templates |
- Dynamic Tests |

---

### First Jupiter Test

```java
import org.junit.jupiter.api.*;

class FirstJUnit5Tests {

    @Test
    void myFirstTest() {
        Assertions.assertEquals(2, 1 + 1, "2 is two");
    }

}
```

@[1](Import JUnit Jupiter API)
@[3,6](Use 'package-private' modifier)
@[5-8](@Test-annotated method, also 'package-private')

+++

### More Core Annotations

+++

### Meta-Annotations

```java
@Tag("fast")
@Tag("system")
@Test
@interface FastSystemTest {}

@FastSystemTest
void mySecondTest() {...} 
```

@[1-2](Multiple tags)
@[3](Mark as test)
@[4,8](Use your meta-annotation)

---

# JPMS

[Modules] are named, self-describing program components consisting of code and data. A module must be able to contain Java classes and interfaces, as organized into packages, and also native code, in the form of dynamically-loadable libraries. A module’s data must be able to contain static resource files and user-editable configuration files.
[http://openjdk.java.net/projects/jigsaw/spec/reqs/02#modules]

---

# What is a module?
- Named
- Set of packages (code and data)
- Module Metadata (module-info.class)

+++

# Simple Jar

- com.example.tool.jar
-   com.example.tool
-   com.example.tool.internal

+++

# Module Descriptor

module-info.java
```java
module com.example.tool {
  exports com.example.tool;
}
```

+++

# Modular Jar

- com.example.tool.jar
- + module-info.class
-   com.example.tool
-   ~com.example.tool.internal~

# Modular World

https://github.com/junit-team/junit5-samples/blob/master/README.md
