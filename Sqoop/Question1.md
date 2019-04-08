Question #1
=============
>
1. From the accounts table, import only the primary key, along with the first name, last name to
HDFS directory /loudacre/accounts/user_info. Please save the file in text format with tab
delimiters.
Hint: You will have to figure out what the name of the table columns are in order to complete
this exercise.


Ansert #1.1
=============
1.1 테이블 정보 조회
-------------
<pre>
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

[training@localhost ~]$
</pre>

1.2 저장
-------------
<pre>
sqoop import \
--table accounts \
--connect jdbc:mysql://localhost/loudacre \
--username training --password training \
--columns "acct_num, first_name, last_name" \
--target-dir /loudacre/accounts/user_info \
--as-textfile \
--fields-terminated-by "\t"

[training@localhost ~]$ sqoop import \
> --table accounts \
> --connect jdbc:mysql://localhost/loudacre \
> --username training --password training \
> --columns "acct_num, first_name, last_name" \
> --target-dir /loudacre/accounts/user_info2 \
> --as-textfile \
> --fields-terminated-by "\t"
19/04/07 23:47:02 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 23:47:02 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 23:47:02 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 23:47:02 INFO tool.CodeGenTool: Beginning code generation
19/04/07 23:47:03 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:47:03 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:47:03 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/9654ca07600d5e06cbae1fdd497705d3/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 23:47:05 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/9654ca07600d5e06cbae1fdd497705d3/accounts.jar
19/04/07 23:47:05 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 23:47:05 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 23:47:05 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 23:47:05 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 23:47:05 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 23:47:05 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 23:47:05 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 23:47:06 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 23:47:06 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 23:47:08 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 23:47:08 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/04/07 23:47:08 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/04/07 23:47:08 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 23:47:09 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554697657866_0007
19/04/07 23:47:09 INFO impl.YarnClientImpl: Submitted application application_1554697657866_0007
19/04/07 23:47:09 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554697657866_0007/
19/04/07 23:47:09 INFO mapreduce.Job: Running job: job_1554697657866_0007
19/04/07 23:47:17 INFO mapreduce.Job: Job job_1554697657866_0007 running in uber mode : false
19/04/07 23:47:17 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 23:47:24 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 23:47:30 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 23:47:35 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 23:47:40 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 23:47:40 INFO mapreduce.Job: Job job_1554697657866_0007 completed successfully
19/04/07 23:47:40 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=560472
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=2615920
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=15660
		Total vcore-seconds taken by all map tasks=15660
		Total megabyte-seconds taken by all map tasks=4008960
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=249
		CPU time spent (ms)=3710
		Physical memory (bytes) snapshot=496340992
		Virtual memory (bytes) snapshot=8262230016
		Total committed heap usage (bytes)=251920384
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=2615920
19/04/07 23:47:40 INFO mapreduce.ImportJobBase: Transferred 2.4947 MB in 34.0225 seconds (75.0859 KB/sec)
19/04/07 23:47:40 INFO mapreduce.ImportJobBase: Retrieved 129761 records.
<pre>
