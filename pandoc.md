# Pandoc 文檔格式轉換工具

-   **Pandoc 官網**： <https://pandoc.org>
-   **下載**： <https://github.com/jgm/pandoc/releases>

Pandoc 號稱文本格式轉換的瑞士軍刀, 可以將文檔在 HTML、
Markdown、DokuWiki、 Emacs Org-Mode、 reStructuredText、 MediaWiki、
LaTeX、 Word、 docx 等各種標記文檔格式之間相互轉換，導入導出操作。

## Pandoc安裝

### Windows 系統

github上不去，可以在校園網聯合鏡像站
<https://mirrors.cernet.edu.cn/list> 搜索下載，有現成的安裝包
pandoc-2.19.2-windows-x86_64.msi , 下載後運行安裝包。

### Linux 系統

對於 Ubuntu 等 Linux 發行版，Pandoc
已經被集成到系統的軟件源內，因此可以直接從軟件源安裝：

    sudo apt install pandoc

或者，如果你已經安裝了 Anaconda，那麼你可以直接使用 Pandoc
了。該程序已經被集成到 Anaconda 中。

## 參數說明

Pandoc 程序的命令使用方式為：

    $ pandoc <files> <options>

其中 \<files\>
為輸入的內容，其輸入即可以來自文件，也可以來自標準輸入甚至網頁鏈接。而
\<options\> 為參數選項。主要的參數選項有：

``` 
-f <format>、-r <format>：指定輸入文件格式，默認為 Markdown；
-t <format>、-w <format>：指定輸出文件格式，默認為 HTML；
-o <file>：指定輸出文件，該項缺省時，將輸出到標準輸出；
--highlight-style <style>：設置代碼高亮主題，默認為 pygments；
-s：生成有頭尾的獨立文件（HTML，LaTeX，TEI 或 RTF）；
-S：聰明模式，根據文件判斷其格式；
--self-contained：生成自包含的文件，僅在輸出 HTML 文檔時有效；
--verbose：開啟 Verbose 模式，用於 Debug；
--list-input-formats：列出支持的輸入格式；
--list-output-formats：列出支持的輸出格式；
--list-extensions：列出支持的 Markdown 擴展方案；
--list-highlight-languages：列出支持代碼高亮的編程語言；
--list-highlight-styles：列出支持的代碼高亮主題；
-v、--version：顯示程序的版本號；
-h、--help：顯示程序的幫助信息。
```

雖然 Pandoc
提供了用於指定輸入輸出格式的參數，但是很多時候該參數不必使用。Pandoc
已經足夠聰明到可以根據文件名判斷輸入輸出格式，所以除非文件名可能造成歧義，否則這兩個參數都可以省略。

## 使用示例

使用 Pandoc 可以很容易地将 Markdown 文档渲染为 HTML、 docx、 PDF
等文档：

``` bash
# 由 Markdown 生成 HTML
$ pandoc demo.md -o demo.html
# 由 Markdown 生成 docx
$ pandoc demo.md -o demo.docx
# 由 Markdown 生成 PDF
$ pandoc demo.md -o demo.pdf
# 由Word docx 生成 Markdown
$ pandoc demo.docx -o demo.md
# 由 HTML 网页生成 Markdow
$ pandoc http://www.demo.com/demo.html -o demo.md
# 由 HTML 文件生成 Dokuwiki
$ pandoc -f html -t dokuwiki demo.html -o demo.txt
# 由 Markdown 生成 Dokuwiki
$ pandoc -f markdown -t dokuwiki demo.md -o demo.txt
# 由 github Markdown 生成 Dokuwiki
$ pandoc -f markdown_github -t dokuwiki demo.md -o demo.txt

# 信息查看
# 查看程序支持的输入文件格式：
$ pandoc --list-input-formats
# 查看程序支持代码高亮的编程语言：
$ pandoc --list-highlight-languages
# 查看程序帮助：
$ pandoc --help
```
