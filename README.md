# Wordpress Database manipulation snippets

A list of SQL queries to make rapid changes in the database of a  WordPress-site

## Credits

Most of these snippets are gathered from different WordPress-related websites and the WordPress forums. I credited the author for each snippets with a link to the source, whenever possible. If you notice that some snippets needs the correct source, please send a pull-request or contact me.

# Table of Contents
- [Migrate WordPress Database](#Migrate WordPress Database)
    -[Change url](#Change url)   
- [Edit Posts & Pages](#Edit Post & Pages)
    - [Close trackbacks and pingbacks](#Close trackbacks and pingbacks)
    - [Close comments](#Close comments)
    - [Set the posts of author A to author B](#Set the posts of author A to author B)

## Migrate WordPress Database
### Change URL
```
//just put in old url and new url
set @oldurl = 'http://oldwp-url.com', @newurl = 'http://newwp-url.com';

UPDATE wp_options SET option_value = replace(option_value, @oldurl, @newurl) WHERE option_name = 'home' OR option_name = 'siteurl';
UPDATE wp_posts SET guid = REPLACE (guid, @oldurl, @newurl);
UPDATE wp_posts SET post_content = REPLACE (post_content, @oldurl, @newurl);
UPDATE wp_posts SET post_content = REPLACE (post_content, CONCAT('src="', @oldurl), CONCAT('src="', @newurl));
UPDATE wp_posts SET guid = REPLACE (guid, @oldurl, @newurl) WHERE post_type = 'attachment';
UPDATE wp_postmeta SET meta_value = REPLACE (meta_value, @oldurl, @newurl);
```
[Source Lucas Serafim](http://www.onextrapixel.com/2010/01/30/13-useful-wordpress-sql-queries-you-wish-you-knew-earlier/#comment-826362117)

## Edit Post & Pages

### Close trackbacks and pingbacks

```
UPDATE wp_posts SET ping_status='closed' WHERE post_status = 'publish' AND post_type = 'post';
UPDATE wp_posts SET ping_status='closed' WHERE post_status = 'publish' AND post_type = 'page';
```
[source](https://wordpress.org/support/topic/globally-disable-pingback-and-trackback)

### Close comments
```
UPDATE wp_posts SET comment_status='closed' WHERE post_status = 'publish' AND post_type = 'post';
UPDATE wp_posts SET comment_status='closed' WHERE post_status = 'publish' AND post_type = 'page';
```
[source](https://wordpress.org/support/topic/globally-disable-pingback-and-trackback)

## Set the posts of author A to author B

```
UPDATE wp_posts SET post_author = 'new-author-id' WHERE post_author = 'old-author-id';
``
[source onextrapixel](http://www.onextrapixel.com/2010/01/30/13-useful-wordpress-sql-queries-you-wish-you-knew-earlier/)

## 
