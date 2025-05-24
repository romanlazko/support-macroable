# Macroable Trait

A PHP trait that enables dynamic method addition to classes at runtime, inspired by Laravel's Macroable trait.

## Installation

You can install the package via Composer:

```bash
composer require romanlazko/support-macroable
```

## Usage

### Basic Macro Registration

```php
use RomanLazko\Support\Traits\Macroable;

class ExampleClass
{
    use Macroable;
}

// Register a macro
ExampleClass::macro('greet', function ($name) {
    return "Hello, {$name}!";
});

// Use the macro
echo ExampleClass::greet('World'); // Output: Hello, World!
```

### Instance Macros

Macros can also be called on class instances:

```php
$example = new ExampleClass();
echo $example->greet('World'); // Output: Hello, World!
```

### Mixin Support

You can mix in multiple methods from another class:

```php
class MyMacros {
    public function greet($name) {
        return "Hello, {$name}!";
    }
    
    public function farewell($name) {
        return "Goodbye, {$name}!";
    }
}

ExampleClass::mixin(new MyMacros);

echo ExampleClass::greet('World'); // Output: Hello, World!
echo ExampleClass::farewell('World'); // Output: Goodbye, World!
```

### Checking for Macros

Check if a macro exists:

```php
if (ExampleClass::hasMacro('greet')) {
    // Macro exists
}
```

### Flushing Macros

Remove all registered macros:

```php
ExampleClass::flushMacros();
```

## Available Methods

- `macro(string $name, callable $macro)`: Register a new macro
- `mixin(object $mixin, bool $replace = true)`: Mix in methods from another class
- `hasMacro(string $name): bool`: Check if a macro exists
- `flushMacros()`: Remove all registered macros

## Requirements

- PHP 7.4 or higher

## License

This package is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.