# Serializable Closure

<a href="https://github.com/Harmony/serializable-closure/actions">
    <img src="https://github.com/Harmony/serializable-closure/workflows/tests/badge.svg" alt="Build Status">
</a>
<a href="https://packagist.org/packages/Harmony/serializable-closure">
    <img src="https://img.shields.io/packagist/dt/Harmony/serializable-closure" alt="Total Downloads">
</a>
<a href="https://packagist.org/packages/Harmony/serializable-closure">
    <img src="https://img.shields.io/packagist/v/Harmony/serializable-closure" alt="Latest Stable Version">
</a>
<a href="https://packagist.org/packages/Harmony/serializable-closure">
    <img src="https://img.shields.io/packagist/l/Harmony/serializable-closure" alt="License">
</a>

## Introduction

> This project is a fork of the excellent [opis/closure: 3.x](https://github.com/opis/closure) package. At Harmony, we decided to fork this package as the upcoming version [4.x](https://github.com/opis/closure) is a complete rewrite on top of the [FFI extension](https://www.php.net/manual/en/book.ffi.php). As Harmony is a web framework, and FFI is not enabled by default in web requests, this fork allows us to keep using the `3.x` series while adding support for new PHP versions.

Harmony Serializable Closure provides an easy and secure way to **serialize closures in PHP**.

## Official Documentation

### Installation

> **Requires [PHP 7.4+](https://php.net/releases/)**

First, install Harmony Serializable Closure via the [Composer](https://getcomposer.org/) package manager:

```bash
composer require Harmony/serializable-closure
```

### Usage

You may serialize a closure this way:

```php
use Harmony\SerializableClosure\SerializableClosure;

$closure = fn () => 'james';

// Recommended
SerializableClosure::setSecretKey('secret');

$serialized = serialize(new SerializableClosure($closure));
$closure = unserialize($serialized)->getClosure();

echo $closure(); // james;
```

### Caveats

* Anonymous classes cannot be created within closures.
* Attributes cannot be used within closures.
* Serializing closures on REPL environments like Harmony Tinker is not supported.
* Serializing closures that reference objects with readonly properties is not supported.

## Contributing

Thank you for considering contributing to Serializable Closure! The contribution guide can be found in the [Harmony documentation](https://Harmony.com/docs/contributions).

## Code of Conduct

In order to ensure that the Harmony community is welcoming to all, please review and abide by the [Code of Conduct](https://Harmony.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

Please review [our security policy](https://github.com/Harmony/serializable-closure/security/policy) on how to report security vulnerabilities.

## License

Serializable Closure is open-sourced software licensed under the [MIT license](LICENSE.md).
