# Classes and objects in PHP
PHP treats objects in the same way as references or handles, meaning that each variable contains an object reference rather than a copy of the entire object.

Class name regular expression: `^[a-zA-Z_\x7f-\xff][a-zA-Z0-9_\x7f-\xff]*$`

##Properties(variables and constants) and methods(functions)

```php
class Person {

  // const declaration
  const FEET_NUM = 2;
  // properties declaration
  // must be a constant value(can be evaluated at compile time)
  // can be public, protected, private
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
    return self::FEET_NUM;
  }
}
```
## object assignment

```php
$me = new Person();// possible: $class_name = 'Person'; $me = new $class_name();
$me_alias = &$me;
$me_too = $me;

$me_alias = null; // $me and $me_alias is NULL now
```
## class extends

```php
class Parent {
  public function get_name() { return 'parent->'; }
}
class Child extends Parent {
  // override: should use the same parameter signature as the parent
  // except for __construct() and so on
  // NOTE:no overload in PHP
  public function get_name() { return parent::get_name() . ' child->'; }
}
```
## Class autoload (spl_autoload_register() and __autoload())

#### NOTE: 
- __autoload is discouraged and may be deprecated or removed in the future
- autoloading is not avaliable when PHP is used in CLI interactive mode

## Constructors and destructors

#### NOTE:
- You can override __construct() without the same parameter signature as **Parent Class**
- __destruct() can not have parameters
- parent constructors and destructors will not be called implicitly.we would have to explicitly call parent::__**struct() 

```php
class Parent {
  public function __construct() {
    echo 'Parent object initialized';
  }
}

class Child extends Parent {
  public function __construct() {
    parent::__construct();
    echo 'Child object initialized';
  }
}
```
