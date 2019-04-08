Question #3
=============

3. Finally	save	in	/loudacre/accounts/CA	only	clients	whose	state	is	from	California.		Save	the	file in	avro format	and	compressed	using	snappy.		From	the	terminal,	display	some	of	the	records	that	you	just	imported.		Take	a	screenshot	and	save	it	as	CA_only.

Ansert #3.1
=============
3.1 save in /loudacre/accounts/CA only clients whose state is from California.
--------------
<pre>

[training@localhost ~]$ sqoop import \
> --table accounts \
> --connect jdbc:mysql://localhost/loudacre \
> --username training --password training \
> --columns "acct_num, first_name, last_name" \
> --where "state='CA'" \
> --target-dir /loudacre/accounts/CA2 \
> --as-avrodatafile \
> --fields-terminated-by "\t" \
> --compression-codec org.apache.hadoop.io.compress.SnappyCodec
19/04/08 01:38:00 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/08 01:38:00 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/08 01:38:00 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/08 01:38:00 INFO tool.CodeGenTool: Beginning code generation
19/04/08 01:38:01 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/08 01:38:01 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/08 01:38:01 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/a0efc76c0883f4f75b7ce06e190fa050/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/08 01:38:03 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/a0efc76c0883f4f75b7ce06e190fa050/accounts.jar
19/04/08 01:38:03 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/08 01:38:03 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/08 01:38:03 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/08 01:38:03 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/08 01:38:03 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/08 01:38:03 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/08 01:38:03 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/08 01:38:04 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/08 01:38:04 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/08 01:38:04 INFO mapreduce.DataDrivenImportJob: Writing Avro schema file: /tmp/sqoop-training/compile/a0efc76c0883f4f75b7ce06e190fa050/accounts.avsc
19/04/08 01:38:04 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/08 01:38:04 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/08 01:38:06 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/08 01:38:06 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts` WHERE ( state='CA' )
19/04/08 01:38:06 INFO db.IntegerSplitter: Split size: 32439; Num splits: 4 from: 1 to: 129760
19/04/08 01:38:06 INFO mapreduce.JobSubmitter: number of splits:4
19/04/08 01:38:06 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554697657866_0009
19/04/08 01:38:06 INFO impl.YarnClientImpl: Submitted application application_1554697657866_0009
19/04/08 01:38:06 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554697657866_0009/
19/04/08 01:38:06 INFO mapreduce.Job: Running job: job_1554697657866_0009
19/04/08 01:38:13 INFO mapreduce.Job: Job job_1554697657866_0009 running in uber mode : false
19/04/08 01:38:13 INFO mapreduce.Job:  map 0% reduce 0%
19/04/08 01:38:20 INFO mapreduce.Job:  map 25% reduce 0%
19/04/08 01:38:26 INFO mapreduce.Job:  map 50% reduce 0%
19/04/08 01:38:32 INFO mapreduce.Job:  map 75% reduce 0%
19/04/08 01:38:38 INFO mapreduce.Job:  map 100% reduce 0%
19/04/08 01:38:38 INFO mapreduce.Job: Job job_1554697657866_0009 completed successfully
19/04/08 01:38:38 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=563560
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=1350990
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=16724
		Total vcore-seconds taken by all map tasks=16724
		Total megabyte-seconds taken by all map tasks=4281344
	Map-Reduce Framework
		Map input records=92416
		Map output records=92416
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=258
		CPU time spent (ms)=6390
		Physical memory (bytes) snapshot=626388992
		Virtual memory (bytes) snapshot=8298668032
		Total committed heap usage (bytes)=251920384
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=1350990
19/04/08 01:38:38 INFO mapreduce.ImportJobBase: Transferred 1.2884 MB in 34.0471 seconds (38.75 KB/sec)
19/04/08 01:38:38 INFO mapreduce.ImportJobBase: Retrieved 92416 records.

</pre>

3.2 Hue Screen shot
-------------
<img src = "https://github.com/shkim99/SKCC2_-BigData/blob/master/Sqoop/CA_only.PNG?raw=true">
