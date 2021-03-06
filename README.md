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

## Challenge 6
Today's Regex Tuesday challenge, the sixth challenge, is to match IPv4 addresses in the syntaxes (dotted decimal, dotted hexadecimal, dotted octal, hexadecimal, decimal and octal) specified on Wikipedia. More test cases will be added to this challenge later.  
`/^(((\d{1,2})|([01]\d{2})|(2[0-4]\d)|25[0-5]|0x[0-9a-fA-F][0-9a-fA-F]?|0[0-3][0-7][0-7])(\.|$)){4}/i`  
`0[0-3][0-7]{,10}|0x[0-9a-fA-F]{0,8}|[1-3][0-9]{0,9}|4[01]\d{8}|42[0-8]\d{7}`  
`/^(((\d{1,2})|([01]\d{2})|(2[0-4]\d)|25[0-5]|0x[0-9a-fA-F][0-9a-fA-F]?|0[0-3][0-7][0-7])(\.(?!$)|$)){4}$|^(0[0-3][0-7]{0,10})$|^(0x[0-9a-fA-F]{0,8})$|^([1-3][0-9]{0,9})$|(4[01]\d{8}|42[0-8]\d{7}|429[0-3]\d{6}|4294[0-8]\d{5}|42949[0-5]\d{4}|429496[0-6]\d{3}|4294967[0-1]\d{2}|42949672[0-8]\d{1}|429496729[0-5])/i`

## Challenge 7
The seventh regex tuesday challenge is to match valid domain names with protocols (http and https) in front of them and an optional slash (/) behind them. To keep it simple, you do not have to worry about special characters.  
`/^(https?):\/\/(?!-)([\w]{1,30}[-\.]){1,40}\w+\/?$/i`  
`/^(https?):\/\/(?!-)([a-z0-9A-Z]{1,30}[-\.]){1,40}\w+\/?$/i`  
`/^(https?):\/\/([a-z0-9A-Z]{1,30}[-\.]){1,40}\w+\/?$/i`  

## Challenge 8
This challenge is a hybrid of challenge #1 - matching repeated words - and challenge #4, a basic MarkDown parser. The challenge is to match (immediately) repeating MarkDown list items! Check out the examples - it is easier to look at them than to have it explained.  

Repeated items should be wrapped in double asterisks, for MarkDown bold. The second * List item should be replaced with * **List item**  
`/(\*\s*([\*\s\w]+)\n\*\s*)(\2)/i`  
`$1**$3**`

`/(\*\s*([\*\s\w]+)\n\*\s*)(\2)(?=\n|$)/ig`
`$1**$3**`  

## Challenge 9
Another MarkDown challenge! This challenge is simply to parse MarkDown links - so [text](http://example.com) would simply be replaced with the following HTML: <a href="http://example.com">text</a>.

Be careful with images. ![alt text](image location) should be left alone, as it isn't a link.

If you don't want to write an expression for URLs too, you can see answers to the previous challenge on URLs on Reddit.

`/([\w\s:]*)\[([\s\w\.!]*)\]\(((https?):\/\/([a-z0-9A-Z]{1,30}[-\.]){1,40}\w+\/?)\)/i`  `$1<a href="$3">$2</a>`

`/([\w\s:]*)( |^)\[([\s\w\.!]*)\]\(((https?):\/\/([a-z0-9A-Z]{1,30}[-\.]){1,40}\w+\/?)\)(?!\w)/i`  `$1$2<a href="$4">$3</a>`
