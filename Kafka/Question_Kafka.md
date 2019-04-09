Question
=============
>
1. Open a new gateway terminal window on your Get2Cluster remote desktop and create a Kafka
topic named weblogs that will contain messages representing lines in Loudacre’s web server
logs.

Ansert #1
=============
<pre>
[training@localhost scripts]$ kafka-topics --create \
> --zookeeper localhost:2181 \
> --replication-factor 1 \
> --partitions 1 \
> --topic weblogs
Created topic "weblogs".
[training@localhost scripts]$

</pre>
Question 2
=============
2. Display all Kafka topics to confirm that the new topic you just created is listed:

Ansert #2
=============
<pre>
[training@localhost scripts]$ kafka-topics --list \
> --zookeeper localhost:2181
weblogs
[training@localhost scripts]$
<pre>

Question 3
=============
3. Review the details of the weblogs topic.

Ansert #3
=============
<pre>
[training@localhost scripts]$ kafka-topics --describe weblogs \
> --zookeeper localhost:2181
Topic:weblogs	PartitionCount:1	ReplicationFactor:1	Configs:
	Topic: weblogs	Partition: 0	Leader: 0	Replicas: 0	Isr: 0
[training@localhost scripts]$

<pre>

Question 4
=============
4. Start a Kafka producer for the weblogs topic:

Ansert #4
=============
<pre>
[training@localhost scripts]$ kafka-console-producer \
> --broker-list localhost:9092 \
> --topic weblogs

<pre>

Question 5
=============
5. Publish a test message to the weblogs topic by typing the message text and then pressing
Enter. For example:

Ansert #5
=============
<pre>
[training@localhost ~]$ kafka-console-producer \
> --broker-list localhost:9092 \
> --topic weblogs




test weblog entry 1

<pre>
Question 6
=============
6. Open a new terminal window and adjust it to fit on the window beneath the producer window.
Set the title for this window to “Kafka Consumer.”
Question 7
=============
7. In the new gateway terminal window, start a Kafka consumer that will read from the beginning
of the weblogs topic:

Ansert #6 7
=============
<pre>
[training@localhost ~]$ kafka-console-consumer \
> --zookeeper localhost:2181 \
> --topic weblogs \
> --from-beginning





test weblog entry 1


<pre>
Question 8
=============
8. Press Ctrl+C to stop the weblogs consumer, and restart it, but this time omit the --frombeginning
option to this command. You should see that no messages are displayed.

Ansert #8
=============
<pre>
[training@localhost ~]$ kafka-console-consumer \
> --zookeeper localhost:2181 \
> --topic weblogs


<pre>
Question 9  10
=============
9. Switch back to the producer window and type another test message into the terminal, followed
by the Enter key:
10. Return to the consumer window and verify that it now displays the alert message you
published from the producer in the previous step.
Ansert #9 10
=============
<pre>
[training@localhost ~]$ kafka-console-producer \
> --broker-list localhost:9092 \
> --topic weblogs




test weblog entry 1



test weblog entry 2


[training@localhost ~]$ kafka-console-consumer \
> --zookeeper localhost:2181 \
> --topic weblogs



test weblog entry 2


<pre>
Question 10
=============


Ansert #10
=============
<pre>

<pre>
