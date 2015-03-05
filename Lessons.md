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
