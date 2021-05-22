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

* `(?sw)(.+?)\b`

**note**: (?w) lets \b match at [UAX#29](https://www.unicode.org/reports/tr29/) text boudaries

```
C_LONGINT($i)
ARRAY LONGINT($pos;0)
ARRAY LONGINT($len;0)

$i:=1

$text:="Your balance is $1,234.56... I think."
$words:=New collection

While (Match regex("(?sw)(.+?)\\b";$text;$i;$pos;$len))
	$word:=Substring($text;$pos{1};$len{1})
	If (Match regex("\\w+";$word;1))
		$words.push($word)
	End if 
	$i:=$pos{1}+$len{1}
End while 

  //["Your","balance","is","1,234.56","I","think"]
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
