# 1.) A visitor counter
Create a php file that outputs "You are visitor: _$n_" (where _$n_ is the number of page hits) using the following functions:

* `file_exists`
* `file_get_contents`
* `file_put_contents`
* `echo`

## Unique hit variant
Only add to the page hit counter if this IP address has never been seen before. Record the seen IP's in a separate data file.

### Read:
* [$_SERVER][1]
* [Superglobals][2]

[1]: http://php.net/manual/en/reserved.variables.server.php
[2]: http://php.net/manual/en/language.variables.superglobals.php

### Also use functions:
* `in_array`
* `serialize` and `unserialize` (easier), or
* `pack`, `unpack` and `ip2long` (more challenging)

# 2.) A comments form
* `view-comments.php`: Outputs the comments stored in a data file, along with a form to post new comments. Displays a friendly message if no comments.
* `post-comment.php`: Appends a new comment to the data file, and redirects to `view-comments.php` if successful. Displays a friendly error message if the `comment` parameter is missing.

### Read:
* [$_POST] [3]
* [User Submitted Data] [4]

[3]: http://php.net/manual/en/reserved.variables.post.php
[4]: http://php.net/manual/en/security.variables.php

### Use functions:
* `empty`
* `htmlspecialchars`
* `file_exists`
* `file_get_contents`
* `file_put_contents`
* `serialize`
* `unserialize`
* `header`

## Object-Oriented variant
Instead of using a hard-coded data file name to store the comments, implement the following interface in a class to manipulate _$articleID_.dat

```php
<?php

interface ArticleCommentInterface {
  public function __construct($articleID);
  public function getComments();
  public function addComment($comment);
}
```

### Read:
* [Filesystem Security] [FILE_SEC]
* [Classes and Objects: The Basics] [CLASS_BASICS]
* [Classes and Objects: Properties] [CLASS_PROPERTIES]
* [Classes and Objects: Constructors and Deconstructs] [CLASS_CONSTRUCTORS]
* [Classes and Objects: Object Interfaces] [CLASS_INTERFACES]

[FILE_SEC]: http://php.net/manual/en/security.filesystem.php
[CLASS_BASICS]: http://php.net/manual/en/language.oop5.basic.php
[CLASS_PROPERTIES]: http://php.net/manual/en/language.oop5.properties.php
[CLASS_CONSTRUCTORS]: http://php.net/manual/en/language.oop5.decon.ph
[CLASS_INTERFACES]: http://php.net/manual/en/language.oop5.interfaces.php

# 3.) Now with MySQL
Repeat lessons 1 and 2, but with MySQL database server to replace the data files. Should display the error message from DB server on connection or query error. For extra fun, use the object-oriented mysqli interface.

### Read:
* [Database Security: SQL Injection] [SQL_INJECTION]
* [MySQLi: Dual procedural and object-oriented interface] [5]
* [3.3 Creating and Using a Database] [6]

[SQL_INJECTION]: http://php.net/manual/en/security.database.sql-injection.php
[5]: http://php.net/manual/en/mysqli.quickstart.dual-interface.php
[6]: http://dev.mysql.com/doc/refman/5.6/en/database-use.html

### Use functions:
 * `mysqli_connect`
 * `mysqli_connect_errno`
 * `mysqli_connect_error`
 * `mysqli_query`
 * `mysqli_real_escape_string`
 * `mysqli_error`
 * `mysqli_fetch_assoc`
 * `mysqli_free_result`
 * `mysqli_close`
 
## Prepared Statement Variant
Instead of using `mysqli_query` and `mysqli_real_escape_string`, use the following functions:
 * `mysqli_stmt_init`
 * `mysqli_stmt_bind_param`
 * `mysqli_stmt_prepare`
 * `mysqli_stmt_execute`
 * `mysqli_stmt_bind_result`
 * `mysqli_stmt_fetch`
 * `mysqli_stmt_close`
