﻿**base knowledge**
-------------
### 关于正则表达式:

 1. 正则表达式,(?<=...)之前的字符串需要匹配表达式才能成功匹配.不消耗字符串内容.<br>
正则表达式,(?=...)之后的字符串需要匹配表达式才能成功匹配.不消耗字符串内容.
>如:`pattern = re.compile(r'(?<=[>"])test(?=[<"])')`<br>
这正则表示当test字符串左右两边均为`[>"]`中的其中一个字符时才能匹配成功.

 2. 正则表达式,`(?<!...)`之前的字符串需要不匹配表达式才能成功匹配.不消耗字符串内容.<br>
正则表达式,`(?!...)`之后的字符串需要不匹配表达式才能成功匹配.不消耗字符串内容.

 3. 匹配形如”///abc”的字符串,要求只按最后一个/进行split<br>
    `b = re.split(‘/(?!/)’,a)`

 4. `re.IGNORECASE`<br>
让正则表达式忽略大小写，这样一来，[A-Z]也可以匹配小写字母了。
 5. re.DOTALL<br>
影响'.'的行为，平时'.'匹配除换行符以外的所有字符，指定了本标志以后，也可以匹配换行符。

 5. List item
