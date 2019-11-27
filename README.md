# Purpose

Provide a regex pattern that will match an entire string if, anywhere within the string, it contains an unescaped single quote. An "escaped single quote" is defined as two consecutive quotes. 

I use this regex to help detect malformed inputs, aka input sanitization, for SQL queries.

Put another way, this will match an entire string if, anywhere within the string, there is an odd number (1, 3, 5, etc) of adjacent single quotes. 

## Regex

This was provided by a colleague and regex wizard, Nicolas Moutschen. Big thanks to Nicolas, my regex skills are not as savvy :)

```
^.*(?<!')'('')*(?!').*$
```

## Examples

You can test this out on https://regex101.com/

### Matches

This should match the entire string from any of these examples: 

  ```
  This is a ' test
  ```

  ```
  This ' is another ' test
  ```

  ```
  This is a ''' test that has one escaped quote and one adjacent unescaped quote
  ```

  ```
  This matches if, anywhere within the string, there is ' an odd number of ''''' quotes
  ```
