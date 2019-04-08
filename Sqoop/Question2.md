Question #2
=============

2. This time save the same in parquet format with snappy compression. Save it in
/loudacre/accounts/user_compressed. Provide.a screenshot of HUE with the new directory
created.


Ansert #2.1
=============
2.1 save the same in parquet format with snappy compression
--------------
<pre>

[training@localhost ~]$ sqoop import \
> --table accounts \
> --connect jdbc:mysql://localhost/loudacre \
> --username training --password training \
> --columns "acct_num, first_name, last_name" \
> --target-dir /loudacre/accounts/user_compressed2 \
> --as-parquetfile \
> --fields-terminated-by "\t" \
> --compression-codec org.apache.hadoop.io.compress.SnappyCodec
19/04/08 01:31:44 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/08 01:31:44 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/08 01:31:44 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/08 01:31:44 INFO tool.CodeGenTool: Beginning code generation
19/04/08 01:31:44 INFO tool.CodeGenTool: Will generate java class as codegen_accounts
19/04/08 01:31:45 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/08 01:31:45 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/08 01:31:45 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/b4ddc5b698c2ca163fde2b5352de7f79/codegen_accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/08 01:31:47 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/b4ddc5b698c2ca163fde2b5352de7f79/codegen_accounts.jar
19/04/08 01:31:47 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/08 01:31:47 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/08 01:31:47 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/08 01:31:47 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/08 01:31:47 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/08 01:31:47 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/08 01:31:47 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/08 01:31:48 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/08 01:31:48 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/08 01:31:49 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/08 01:31:49 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/08 01:31:51 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/08 01:31:51 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/04/08 01:31:51 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/04/08 01:31:51 INFO mapreduce.JobSubmitter: number of splits:4
19/04/08 01:31:52 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554697657866_0008
19/04/08 01:31:52 INFO impl.YarnClientImpl: Submitted application application_1554697657866_0008
19/04/08 01:31:52 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554697657866_0008/
19/04/08 01:31:52 INFO mapreduce.Job: Running job: job_1554697657866_0008
19/04/08 01:32:00 INFO mapreduce.Job: Job job_1554697657866_0008 running in uber mode : false
19/04/08 01:32:00 INFO mapreduce.Job:  map 0% reduce 0%
19/04/08 01:32:08 INFO mapreduce.Job:  map 25% reduce 0%
19/04/08 01:32:15 INFO mapreduce.Job:  map 50% reduce 0%
19/04/08 01:32:22 INFO mapreduce.Job:  map 75% reduce 0%
19/04/08 01:32:29 INFO mapreduce.Job:  map 100% reduce 0%
19/04/08 01:32:29 INFO mapreduce.Job: Job job_1554697657866_0008 completed successfully
19/04/08 01:32:29 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=565924
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=25274
		HDFS: Number of bytes written=1305047
		HDFS: Number of read operations=272
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=40
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=22499
		Total vcore-seconds taken by all map tasks=22499
		Total megabyte-seconds taken by all map tasks=5759744
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=525
		CPU time spent (ms)=8390
		Physical memory (bytes) snapshot=673083392
		Virtual memory (bytes) snapshot=8296194048
		Total committed heap usage (bytes)=251920384
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=0
19/04/08 01:32:29 INFO mapreduce.ImportJobBase: Transferred 1.2446 MB in 39.5382 seconds (32.2337 KB/sec)
19/04/08 01:32:29 INFO mapreduce.ImportJobBase: Retrieved 129761 records.
[training@localhost ~]$

</pre>

2.2 Hue Screen shot
-------------
<img src = "https://github.com/shkim99/SKCC2_-BigData/blob/master/Sqoop/question2.PNG?raw=true">
