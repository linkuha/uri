`parse_url($url)` function and `filter_var($url, FILTER_VALIDATE_URL)` are weak for parsing and validating purposes.

Usage example:
```$xslt
$myValidator = (new HttpValidator())
    ->allowLocalDomain()
    ->allowLocalIp()
    ->allowWithoutScheme()
    ->allowPunycode(true);

$validStatus = true;
$parsedParts = [];

if (! $myValidator->isSecure($url)) {
    $validStatus = false;
}
if (false === ($parsedParts = $myValidator->parseUrl($url))) {
    $validStatus = false;
}
$fix = $myValidator->suggestFix($parsedParts);
```

You can use UriParser separately or extend AbstractValidator with builder design pattern to custom own.

UriHelper contains URI manipulating static things (not all are fullness tested).

You can use any another libraries. For ex.: 
`zendframework/zend-uri`, `symfony/validator`, `league/uri-parser`, `guzzlehttp/guzzle`. For URI normalizing purpose the Guzzle is win by my opinion (tests). 

For parsing/validating purposes no one of these are not fullness correctly validate all my test valid/invalid URLs set (will attach later).