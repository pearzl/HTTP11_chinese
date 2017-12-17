#### 语言标签

语言标签（在RFC5646中定义）指示人类所说的，书面的或以其他方式传达的用于向其他人传递信息的自然语言。计算机语言显然被排除。

HTTP在Accept-Language和Content-Language头字段中使用语言标签。Accept-Language使用5.3.5节定义的更宽泛的language-rang产生式，而Content-Language使用下面的定义的language-tag产生式。

> ```
>      language-tag = <Language-Tag, see [RFC5646], Section 2.1>
> ```

一个语言标签是一个或多个不区分大小写的自标签序列，使用连字符（“-”，%x2D）分隔。大多数情况下，语言标签由标识一个广泛的相关语言的主要语言子标签组成（例如，“en”即英语），可选择地在后面跟随一系列提炼或缩小语言范围的子标签。（例如，“en-CA”即在加拿大交流使用的英语类型）。语言标签中不允许空白。例子标签包括：
>  fr, en-US, es-419, az-Arab, x-pig-latin, man-Nkoo-GN

查看RFC5646了解更多信息。


#### Content-Language

“Content-Language”头字段为表示描述了目的观众的自然语言。请注意，这可能不等同于表示中使用的所有语言。

> ```
>     Content-Language = 1#language-tag
> ```

语言标签被定义在3.1.3.1节。Content-Language的主要目的是允许用户通过用户自己青睐的语言识别和区分标识表示。因此，如果内容只打算给懂丹麦语的观众，合适的字段是
> ```
>     Content-Language: da
> ```

如果Content-Language没有制定，默认的，内容是给所有语言的观众的。这可能意味着发送者不考虑它为任何特定的自然语言，或者发送者不知道他的目标语言。

多语言**可能**被列出，它是为多种观众准备的。例如，“怀唐伊条约”的翻译同时以原始的毛利语和英语版本呈现，将是这样
> ```
>      Content-Language: mi, en
> ```

但是仅仅因为多个语言出现在表示中并不意味着它是为多种语言的观众提供的。一个例子是某个语言初学者的入门书，例如“A First Lesson in Latin”显然是为懂英语的观众准备的。这种情况下，Content-Language将正确的仅仅包含“en”。

Content-Language可以被用于任何媒体类型，而不仅仅限于文本文档。