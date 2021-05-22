# 4d-tips-get-text-keywords
Different ways to get text keywords

* `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}]+`

```4d
C_LONGINT($i)
ARRAY LONGINT($pos;0)
ARRAY LONGINT($len;0)

$i:=1

$text:="Your balance is $1,234.56... I think."
$words:=New collection

While (Match regex("([\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lo}\\p{Nd}]+)";$text;$i;$pos;$len))
	$word:=Substring($text;$pos{1};$len{1})
	$words.push($word)
	$i:=$pos{1}+$len{1}
End while 

  //["Your","balance","is","1","234","56","I","think"]
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

```4d
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

* `(\\w+)`

```4d
C_LONGINT($i)
ARRAY LONGINT($pos;0)
ARRAY LONGINT($len;0)

$i:=1

$text:="Your balance is $1,234.56... I think."
$words:=New collection

While (Match regex("(\\w+)";$text;$i;$pos;$len))
	$word:=Substring($text;$pos{1};$len{1})
	$words.push($word)
	$i:=$pos{1}+$len{1}
End while 

  //["Your","balance","is","1","234","56","I","think"]

SET TEXT TO PASTEBOARD(JSON Stringify($words))
```

* break using keyword index

```
GET TEXT KEYWORDS // or DISTINCT VALUES with keyword index
```
