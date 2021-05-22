# 4d-tips-get-text-keywords
Different ways to get text keywords

[https://www.unicode.org/reports/tr29/](https://www.unicode.org/reports/tr29/)

* break using regex p (property)

```
[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lo}\\p{Nd}]+
```
