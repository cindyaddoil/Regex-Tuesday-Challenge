# Regex-Tuesday-Challenge
http://callumacrae.github.io/regex-tuesday/

## Challenge 1
You should just wrap the repeated word in a \<strong> element. For example, this is is a test should be turned into this is \<strong>is\</strong> a test.  
`/\b(\S+) (\1)\b/ig`
`$1 \<strong>$2\</strong>`

## Challenge 2
In this challenge, you are aiming to match a grayscale CSS colour. It should be able to match anything but the colour names (eg "red")  
`/^#([0-9a-f]{1,2})\1\1$|^rgb\((\d+\.?\%?\d*),\s*0*\2,\s*0*\2\)$|^rgba\((\d+\%*),\s*\3,\s*\3,.*\)$|^hsl\(\d+\.*\d*,(?:(?:\s*0%,\s*\d+%)|(?:\s\d+\.*\d*%,\s*(10)?0%))\)$|^hsla\(\d+\.*\d*,(?:(?:\s*0%,\s*\d+%)|(?:\s\d+\.*\d*%,\s*(10)?0%))\,.*\)$/i `
