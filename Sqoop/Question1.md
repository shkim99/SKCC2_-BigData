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



1.2 저장
-------------
