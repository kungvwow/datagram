# Datagram component

[![Build Status](https://travis-ci.org/reactphp/datagram.svg?branch=master)](https://travis-ci.org/reactphp/datagram) [![Code Climate](https://codeclimate.com/github/reactphp/datagram/badges/gpa.svg)](https://codeclimate.com/github/reactphp/datagram)

Event-driven UDP datagram socket client and server for [ReactPHP](http://reactphp.org)

## Quickstart example

Once [installed](#install), you can use the following code to connect to an UDP server listening on
`localhost:1234` and send and receive UDP datagrams:  

```php
$loop = React\EventLoop\Factory::create();

$factory = new React\Datagram\Factory($loop);

$factory->createClient('localhost:1234')->then(function (React\Datagram\Socket $client) {
    $client->send('first');

    $client->on('message', function($message, $serverAddress, $client) {
        echo 'received "' . $message . '" from ' . $serverAddress. PHP_EOL;
    });
});

$loop->run();
```

See also the [examples](examples).

## Usage

This library's API is modelled after node.js's API for
[UDP / Datagram Sockets (dgram.Socket)](http://nodejs.org/api/dgram.html).

## Install

The recommended way to install this library is [through Composer](http://getcomposer.org).
[New to Composer?](http://getcomposer.org/doc/00-intro.md)

```bash
$ composer require react/datagram:^1.2
```

See also the [CHANGELOG](CHANGELOG.md) for details about version upgrades.

## Tests

To run the test suite, you first need to clone this repo and then install all
dependencies [through Composer](http://getcomposer.org):

```bash
$ composer install
```

To run the test suite, go to the project root and run:

```bash
$ php vendor/bin/phpunit
```

## License

MIT
