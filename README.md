# Wordpress Database manipulation snippets

A list of SQL queries to make rapid changes in the database of a  WordPress-site

## Credits

Most of these snippets are gathered from different WordPress-related websites and the WordPress forums. I credited the author for each snippets with a link to the source, whenever possible. If you notice that some snippets needs the correct source, please send a pull-request or contact me.

# Table of Contents

- [wp_posts](#Close trackbacks and pingbacks)
    - [Close trackbacks and pingbacks](#Close trackbacks and pingbacks)
    - [Close comments](#Close comments)

# Close trackbacks and pingbacks

```
UPDATE wp_posts SET ping_status='closed' WHERE post_status = 'publish' AND post_type = 'post';
UPDATE wp_posts SET ping_status='closed' WHERE post_status = 'publish' AND post_type = 'page';
```
[source](https://wordpress.org/support/topic/globally-disable-pingback-and-trackback)

#Close comments
```
UPDATE wp_posts SET comment_status='closed' WHERE post_status = 'publish' AND post_type = 'post';
UPDATE wp_posts SET comment_status='closed' WHERE post_status = 'publish' AND post_type = 'page';
```
[source](https://wordpress.org/support/topic/globally-disable-pingback-and-trackback)
