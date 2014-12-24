# Bindex [![Build Status](https://travis-ci.org/gsamokovarov/bindex.svg?branch=master)](https://travis-ci.org/gsamokovarov/bindex)

When Ruby raises an exception, it leaves you backtraces to help you figure out
where did the exception originated in. Bindex gives you the bindings as well.
This can help you introspect the state of the Ruby program when the exception
happened.

## Usage

**Do not** use this gem on production environments. The performance penalty isn't
worth it anywhere outside of development.

### API

Bindex defines the following API:

#### Exception#bindings

Returns all the bindings up to the one in which the exception originated in.

#### Bindex.current_bindings

Returns all of the current Ruby execution state bindings. The first on is the
current one, the second is the caller one, the third is the caller of the
caller one and so on.

## Support

### CRuby

CRuby 1.9.2 and below is **not** supported.

### JRuby

To get the best support, run JRuby in interpreted mode.

```bash
export JRUBY_OPTS=-J-Djruby.compile.mode=OFF

# If you run JRuby 1.7.12 and above, you can use:
export JRUBY_OPTS=--dev
```

### Rubinius

Internal errors like `ZeroDevisionError` aren't caught.

## Credits

Thanks to John Mair for his work on binding_of_caller, which is a huge
inspiration. Thanks to Charlie Somerville for better_errors where the idea
comes from. Thanks to Koichi Sasada for the debug inspector API in CRuby.
