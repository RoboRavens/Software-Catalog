These rules help ensure consistancy for all the different types of names in our code.

| type | formatting | prefix when referencing |
| -- | -- | -- |
| public static final property | SCREAMING_SNAKE_CASE | class name |
| public static property | SCREAMING_SNAKE_CASE | class name |
| public property | PascalCase | this. |
| private property | _camelCase with underscore | none |
| local variable | camelCase  | none |
| method name | camelCase  | this |
| method argument | camelCase  | none |
| class | PascalCase  | none |
  
  
```java
public class Example {
    public static final String PUBLIC_STATIC_FINAL_PROPERTY = "";
    public static String PUBLIC_STATIC_PROPERTY = "";
    public String PublicProperty = "";
    private String _privateProperty = "";

    // method names are camelCase
    // argument variable names are camelCase
    public void methodName(string argumentVariable) {
        string localVariable = "";
        this.PublicProperty = argumentVariable;
        Example.PUBLIC_STATIC_PROPERTY = argumentVariable;
        localVariable = Example.PUBLIC_STATIC_FINAL_PROPERTY;
        _privateProperty = argumentVariable;
    }

    @override
    public void periodic() {
        this.methodName("test");
    }
}
```