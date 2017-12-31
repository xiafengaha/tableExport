# tableExport
将这两个文件替换了官网上的文件就可以PDF导出乱码问题。（改文件字体样式是平方字体）。
PS：若需要引入其他字体请参考这个https://www.cnblogs.com/xrab/p/7210588.html
按照网址的方法可以添加其他的字体文件。但是注意的一点是如果按照上面的网址添加自己需要的字体的时候，需要把tableExport.min.js的它自带的字体替换成自己的字体。
<pre>
 pdfMake.fonts={Roboto:{normal:"Roboto-Regular.ttf",bold:"Roboto-Medium.ttf",italics:"Roboto-Italic.ttf",bolditalics:"Roboto-MediumItalic.ttf"}}

</pre>
上面是tableExport.min.js自带的字体，只需把对应的文件替换成你需要的文件就可以了。（具体可以下载我上面的两个js查找）
下面继续讲解下我使用这个插件遇到的问题。
因为这插件是导出表格的数据，因项目需求，这边数据多了，所以我做了个可以下拉滚动的，将表格头固定。我的做法是重新用了个div做表格头部，然后表格内我就没写thead标签了。之后就出现
<pre>
pdfmake.min.js:5 Uncaught TypeError: Cannot read property 'length' of undefined
    at r.measureTable (pdfmake.min.js:5)
    at pdfmake.min.js:5
    at n.auto (pdfmake.min.js:6)
    at r.measureNode (pdfmake.min.js:5)
    at r.measureVerticalContainer (pdfmake.min.js:5)
    at pdfmake.min.js:5
    at n.auto (pdfmake.min.js:6)
    at r.measureNode (pdfmake.min.js:5)
    at r.measureDocument (pdfmake.min.js:5)
    at i.tryLayoutDocument (pdfmake.min.js:5)
</pre>
还有一个报错是"_minWidth" of undefined，弄了好久最后发现是table的thead没有，最后添加了thead一切正常了。
第一次写这个，写的不详细还请见谅。最后感谢上面网址的作者，
