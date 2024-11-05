# Mantleio-core
easy scenario-coverage tool

Read the YML with the scenarios and look for annotation or test method names.

```yaml
#configuration for a Jira project that describe a java application
java-project-sample:
  TC-1: login with valid email
  TC-2: login with invalid email 
```

```java
#java testing class
import org.junit.jupiter.api.Assertions;
import org.junit.jupiter.api.Test;

public class LoginTest {

    private LoginService loginService = new LoginService();

    @Test
    void testLoginWithValidEmail() {
        // Arrange
        String validEmail = "john@example.com";
        String password = "password123";

        // Act
        boolean isLoggedIn = loginService.login(validEmail, password);

        // Assert
        Assertions.assertTrue(isLoggedIn);
    }

    @Test
    void testLoginWithInvalidEmail() {
        // Arrange
        String invalidEmail = "invalid@example";
        String password = "password123";

        // Act
        boolean isLoggedIn = loginService.login(invalidEmail, password);

        // Assert
        Assertions.assertFalse(isLoggedIn);
    }
}
```

The core service will look by the name on the YAML file for those tests doing some conversion considering each testing tool eg. cammel case conversion, snake case convertion etc.

Tech:
- yaml
- java
- geo db check?
