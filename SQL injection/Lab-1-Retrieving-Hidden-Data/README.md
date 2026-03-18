# Lab: Retrieving Hidden Data (SQL Injection)

## Vulnerability
The `category` parameter in the URL is directly used in a SQL query without validation.

## Exploit
Modified the URL parameter:

' OR 1=1--

## Result
The application returned all products, including unreleased ones.

## Key Point
User input is not properly handled, allowing modification of the query logic.
