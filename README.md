# 4d-tips-get-text-keywords
Different ways to get text keywords

[https://www.unicode.org/reports/tr29/](https://www.unicode.org/reports/tr29/)

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
