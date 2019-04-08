Question #1
=============
>
1. From the accounts table, import only the primary key, along with the first name, last name to
HDFS directory /loudacre/accounts/user_info. Please save the file in text format with tab
delimiters.
Hint: You will have to figure out what the name of the table columns are in order to complete
this exercise.
/>




Ansert #1.1
=============
1.1 테이블 정보 조회
-------------
sqoop eval \
--connect jdbc:mysql://localhost/loudacre \
--username training --password training \
--query "desc accounts

[training@localhost ~]$ sqoop eval \
> --connect jdbc:mysql://localhost/loudacre \
> --username training --password training \
> --query "desc accounts"
19/04/07 23:43:58 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 23:43:58 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 23:43:58 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
---------------------------------------------------------------------------------------------------------
| Field                | Type                 | Null | Key | Default              | Extra                |
---------------------------------------------------------------------------------------------------------
| acct_num             | int(11)              | NO  | PRI | (null)               |                      |
| acct_create_dt       | datetime             | NO  |     | (null)               |                      |
| acct_close_dt        | datetime             | YES |     | (null)               |                      |
| first_name           | varchar(255)         | NO  |     | (null)               |                      |
| last_name            | varchar(255)         | NO  |     | (null)               |                      |
| address              | varchar(255)         | NO  |     | (null)               |                      |
| city                 | varchar(255)         | NO  |     | (null)               |                      |
| state                | varchar(255)         | NO  |     | (null)               |                      |
| zipcode              | varchar(255)         | NO  |     | (null)               |                      |
| phone_number         | varchar(255)         | NO  |     | (null)               |                      |
| created              | datetime             | NO  |     | (null)               |                      |
| modified             | datetime             | NO  |     | (null)               |                      |
---------------------------------------------------------------------------------------------------------
[training@localhost ~]$ 

1.2 저장
-------------
sqoop import \
--table accounts \
--connect jdbc:mysql://localhost/loudacre \
--username training --password training \
--columns "acct_num, first_name, last_name" \
--target-dir /loudacre/accounts/user_info \
--as-textfile \
--fields-terminated-by "\t"
