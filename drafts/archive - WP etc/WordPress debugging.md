#WordPress Debugging

`define( 'WP_DEBUG', true );` by default this will be set to false.

###**WP_DEBUG should not be used on a live site**. 
  
  * It can be dangerous on a live site because text in the PHP notices can reveal details about your code, paths and other information to visitors to your site.


`define('WP_DEBUG_LOG', true);` used with WP_DEBUG to save error messages to debug.log in the /wp-content/

`define('WP_DEBUG_DISPLAY', false);` errors are not shown in the html of your site.

  * true is the default.
   
   
   
  
  
  
  
>References
>[Debugging WordPress: How to use wp_debug](https://premium.wpmudev.org/blog/debugging-wordpress-how-to-use-wp_debug/)

