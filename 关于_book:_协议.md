# 关于 book:// 协议

`book://` 可用于在各个杂志中得跳转.

并且提供动态下载, 并打开某一篇文章的功能, 如以下 URL : 

	book://example.org/whatever/whenever/publication.hpub/filename.html#anchor

NOTE: Baker 4.1 support only a subset of the book protocol features (see below), while Baker 4.0 does not support the book protocol. If you want to take advantege of the full book protocol use version 3.2.x instead.

—

The HPub specification defines a book:// protocol to identify books. Here is an example of the syntax for a book URL:


Two great advantages:

We are able to uniquely identify a book: being a URL the path is unique and it can be used to identify:
a uniquely owned domain (i.e. example.org)
a specific path (i.e. whatever/whenever)
a specific publication (i.e. publication)
format (i.e. hpub)
Once we have identified a book, we can add further elements to the URL, to refer to specific items inside it:
filename (i.e. filename.html)
anchor (i.e. #anchor)
We are able to download a book: the protocol used is the standard HTTP, so you can easily replace book:// with http:// and download the book from that specific location.
Notes:

The specific extension can be omitted: in that scenario, the reading software might try to download the extension that is best suited. Baker will download .hpub files by default, but the book:// protocol is agnostic so it could point also to a .epub version or .mobi version or even a pure textual .html version.
Usage in Baker

Baker understands book:// links inside books. When the user clicks on such a link Baker will automatically download and open the book the link points to, replacing the current book with it.

Baker supports a special URL: when clicked, a link pointing to book://local will go back from a downloaded book to the default book originally contained in the published Baker app.

This will allow:

Manual updates of the current book.
The creation of a lightweight version or some kind of "bookshelf" to download books: the default book in the app will just be a collection of book:// links, allowing the users to download the book they want (using book://local to go back to the "bookshelf" and download another one).
The creation of chains of books, of downloadable references and so on.
From version 4.1 book:// links are associated to the books shelf. When the user clicks on such a link Baker will automatically bring the user back to the shelf, then ...

if the book is available for download the download will start
if the book is already downloaded it will be opened
book://local link is not supported anymore, the user can click on the back button in the navigation bar to return to the shelf. Deeper support for the book protocol (address a single page and a specific anchor) are unavailable.