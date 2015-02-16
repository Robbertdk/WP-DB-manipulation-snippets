# Wordpress Database manipulation snippets

A list of SQL queries to make rapid changes in the database of a  WordPress-site

# Table of Contents

# Close all trackbacks and pingbacks

```
UPDATE wp_posts SET ping_status='closed' WHERE post_status = 'publish' AND post_type = 'page';
UPDATE wp_posts SET ping_status='closed' WHERE post_status = 'publish' AND post_type = 'page';
```

#Close all comments
```
UPDATE wp_posts SET comment_status='closed' WHERE post_status = 'publish' AND post_type = 'post';
UPDATE wp_posts SET comment_status='closed' WHERE post_status = 'publish' AND post_type = 'page';
```
