# A really dumb timetracker

These scripts can be used to track time spent at work during a month and calculate the delta between the time your boss wants you at work and your actual time there.

# Requirements
mysql-server, lua, luasql

# Installation

0. Create a database in your local mysql server and a table
```
 CREATE DATABASE 'timetrackd';
 CREATE TABLE IF NOT EXISTS `daily` (
  `timestamp` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
```

1. Open the scripts and adjust the details required to connect to mysql.

2. Open timetrackd and adjust the Server IP this stuff will ping once a while

4. Drop all your scripts somewhere in your PATH, e.g. /usr/local/bin

5. Run crotab -e and add timetrackd to be run once every N minutes.

```
*/5 * * * * /usr/local/bin/timetrackd
```
6. Use timestat to get an overall stats for the last month and timepending to get info on how much time of this miserable day is left. Adjust the scripts as needed to take extra days into account

# Why no sane configuration files? What is this shit? Why mysql?

Because it's a dirty 15-minute hack. Patches welcome.
