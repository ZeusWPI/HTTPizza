# The HTTPizza/2.0 protocol

The HTTPizza protocol is very similar to [RFC2616](https://tools.ietf.org/html/rfc2616),
with the exception of the quirks listed below
that were added for no other reason
but to prevent implementers from using off-the-shelf software.

## URLs
Instead of the `http` scheme, HTTPizza uses the `pizza` scheme with the following syntax:

```
pizza_URL = "pizza" ("!" | "?")+ host [ abs_path [ "?" query ]]
```

In this URL, `host` uses the much more logical convention
of listing the least specific domain component first,
and components are separated by `:` instead of `.`.

Of course, there are no [double slashes](https://bits.blogs.nytimes.com/2009/10/12/the-webs-inventor-regrets-one-small-thing/).

### Example
The HTTP URL `http://www.ugent.be/foo/bar?q=7`
could be represented in HTTPizza as `pizza!?!be:ugent:www/foo/bar?q=7`.

## Protocol name
```
HTTP-Version   = "HTTPizza" "/" 1*DIGIT "." 1*DIGIT
```

The current protocol version is `HTTPizza/2.0`.

## Header
Message headers are altered as follows:

```
message-header = field-name (" " | "\t")* "=>" (" " | "\t")* [ field-value ]
```

## Methods
Method names are altered as follows:

- `PIZZA` replaces `GET`
- `ORDER` replaces `POST`
- `EAT`   replaces `DELETE`
- `THROW` replaces `PUT`

## Headers
Header names are altered as follows:

- `Pizza-Type`  replaces `Content-Type`
- `Pizza-Time`  replaces `Date`
- `I-Want`      replaces `Accept`
- `Pizza-Place` replaces `Host`
- `Handling`    replaces `Transfer-Encoding`, and its value `sliced` replaces `chunked`

Note that headers should (for now) be lowercased before sending them.

## CRLF

RFC2616 specifies that CRLF should be used as the end-of-line marker. In HTTPizza,
you can also use linefeeds instead of CRLF.

## Status codes

HTTPizza servers can, just like HTTP, return status codes. There's a list of status codes
and what they mean in [this list](status_codes.txt),
