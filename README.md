# Regex-Tuesday-Challenge
http://callumacrae.github.io/regex-tuesday/

## Challenge 1
You should just wrap the repeated word in a \<strong> element. For example, this is is a test should be turned into this is \<strong>is\</strong> a test.  
`/\b(\S+) (\1)\b/ig`
`$1 \<strong>$2\</strong>`

## Challenge 2
In this challenge, you are aiming to match a grayscale CSS colour. It should be able to match anything but the colour names (eg "red")  
`/^#([0-9a-f]{1,2})\1\1$|^rgb\((\d+\.?\%?\d*),\s*0*\2,\s*0*\2\)$|^rgba\((\d+\%*),\s*\3,\s*\3,.*\)$|^hsl\(\d+\.*\d*,(?:(?:\s*0%,\s*\d+%)|(?:\s\d+\.*\d*%,\s*(10)?0%))\)$|^hsla\(\d+\.*\d*,(?:(?:\s*0%,\s*\d+%)|(?:\s\d+\.*\d*%,\s*(10)?0%))\,.*\)$/i `

`/^#([0-9a-f]{1,2})\1\1$|^rgb\((\d+\.?\%?\d*),\s*0*\2,\s*0*\2\)$|^rgba\((\d+\%*),\s*\3,\s*\3,.*\)$|^hsla?\(\d+\.*\d*,(?:(?:\s*0%,\s*\d+%)|(?:\s\d+\.*\d*%,\s*(10)?0%))(?:,\s*.*)?\)$/i`

`/^#([0-9a-f]{1,2})\1\1$|^rgb\(((?:[01]\d{0,2})|(?:2(?:[0-4]\d?)|(?:25[0-5])|2)(?:\.\d)*\%?),\s*0*\2,\s*0*\2\)$|^rgba\((\d+\%*),\s*\3,\s*\3,.*\)$|^hsla?\(\d+\.*\d*,(?:(?:\s*0%,\s*\d+%)|(?:\s\d+\.*\d*%,\s*(10)?0%))(?:,\s*.*)?\)$/i`

## Challenge 3
The third regex tuesday challenge is to match dates in YYYY/MM/DD HH:MM(:SS) format. YYYY should be a year between **1000** and *2012*, and everything else should be a valid month, date, hour, minute and second. The seconds should be optional. Don't worry about leap years, and assume that all months have 30 days.  
`/^((1\d{3})|(200\d|201[012]))\/(0[1-9]|1[012])\/(0[1-9]|[12]\d|30)\s+([01]\d|2[0123]):[0-5]\d:?([0-5]\d)?$/`

## Challenge 4
a MarkDown parser - turn italic MarkDown (*this is italic*) into HTML italic: <em>this is italic</em>. It should not, however, match bold text - text surrounded by multiple asterisks.  
`/(^|[^*])\*([^*].+?[^*])\*(?=[^*]|$)/g`  
`$1<em>$2</em>`

## Challenge 5
The fifth Regex Tuesday challenge is to write a regular expressions which matches correctly formatted (with correct thousand seperators and decimal places). It should be able to match both main number syntaxes (10,000,000.45 and 10 000 000,45), and should not match invalid numbers such as 123.456.789.  
`/^\d{1,3}([ ,]\d{3})*([.,]\d+)?$/i`
