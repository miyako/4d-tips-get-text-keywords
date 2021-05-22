# 4d-tips-get-text-keywords
Different ways to get text keywords

* break using regex meta p

```
[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lo}\\p{Nd}]+
```

* break using regex flags sw and meta bw

```
(?sw)(.+?)\\b\r\\w+
```

* break using regex meta S

```
(\\S+)
```

* break using regex flag sw and meta b

**note**: (?w) lets \b match at [UAX#29](https://www.unicode.org/reports/tr29/) text boudaries

```

(?sw)(.+?)\\b
```

* break using regex flag s and meta b

```
(?s)(.+?)\\b
```

* break using regex flag w

```
(\\w+)
```

* break using keyword index

```
GET TEXT KEYWORDS // or DISTINCT VALUES with keyword index
```
