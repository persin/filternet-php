# Filternet
A simple utility to check whether the given url/domain is blocked in Iran.

## Installation

Install this [package](https://packagist.org/packages/filternet/filternet) via [Composer](https://getcomposer.org/download/):

~~~bash
composer global require filternet/filternet
~~~

or via [cgr](https://github.com/consolidation-org/cgr):

~~~bash
cgr filternet/filternet
~~~

## Usage

#### DNS

~~~bash
filternet check:dns youtube.com -s 8.8.8.8
~~~

Result:

~~~
 2/2 [============================] 100% Done!
+-------------+-----------------+---------+---------------------+
| Domain      | IP              | Status  | Date                |
+-------------+-----------------+---------+---------------------+
| youtube.com | 10.10.34.36     | Blocked | 2016-03-14 01:27:58 |
| YOUTUBE.COM | 173.194.116.195 | Open    | 2016-03-14 01:27:58 |
+-------------+-----------------+---------+---------------------+
~~~

#### HTTP

~~~bash
filternet check:http http://dropbox.com
~~~

Result:

~~~
 100/100 [============================] 100% Done!
+--------------------+------------------------+-------+---------+---------------------+
| Url                | HTTP Response Status   | Title | Status  | Date                |
+--------------------+------------------------+-------+---------+---------------------+
| http://dropbox.com | HTTP/1.0 403 Forbidden | M4-8  | Blocked | 2016-03-14 01:30:18 |
+--------------------+------------------------+-------+---------+---------------------+
~~~

#### TLS SNI (Server Name Indication)

~~~bash
filternet check:sni twitter.com
~~~

~~~
 2/2 [============================] 100% Done!
+-------------+---------+-------------------------------+---------------------+
| SNI Name    | Status  | Error                         | Date                |
+-------------+---------+-------------------------------+---------------------+
| twitter.com | Blocked | SSL: Connection reset by peer | 2016-04-08 00:01:13 |
| TWITTER.COM | Open    | ~UNKNOWN~                     | 2016-04-08 00:01:13 |
+-------------+---------+-------------------------------+---------------------+
~~~


## License

This project is released under the [MIT](https://github.com/alibo/filternet/blob/master/LICENSE) License.
