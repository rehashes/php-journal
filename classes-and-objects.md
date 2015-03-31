# Classes and objects in PHP
PHP treats objects in the same way as references or handles, meaning that each variable contains an object reference rather than a copy of the entire object.

Class name的名命规则的正则表达式为：`^[a-zA-Z_\x7f-\xff][a-zA-Z0-9_\x7f-\xff]*$`

在PHP Class中定义properties(constants and variables)和methods(functions):

```php
class Person {
  // properties declaration
  public $name = 'a default name';
  
  // method declaration
  // this method is non-static and called within a object content.
  // so $this refers to a object
  // and self refer to the class itself and is used to access static properties or methods
  public function description() {
    return $this->name . ' has ' . self::get_feet_number() . ' feet';
  }
  
  // static method declaration
  public static function get_feet_number() {
    return 2;
  }
}
```
## object assignment
```
$me = new Person();// possible: $class_name = 'Person'; $me = new $class_name();
$me_alias = &$me;
$me_too = $me;

$me_alias = null; // $me and $me_alias is NULL now
```
