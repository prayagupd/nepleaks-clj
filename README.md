# nepleaks by prayagupd

## prerequisites

[emacs cider](https://github.com/clojure-emacs/cider#via-packageel)

[lein(ingen)][1] 1.7.0 or above.

[1]: https://github.com/technomancy/leiningen

## installing lein 

[Installing lein 1.7.1 described here](http://prayag-waves.blogspot.com.au/2013/01/installing-lein-on-ubuntu-1210.html)

for lein tasks

```
$ lein help
```

## download dependencies

    lein deps 

which will download all required depemdencies.

But don't forget to configure `~/.m2/settings.xml` if [proxy](http://maven.apache.org/guides/mini/guide-proxies.html) is being used. Have a look at lein [issue#283](https://github.com/technomancy/leiningen/issues/283). 

    <settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">

    <!-- proxies
         | This is a list of proxies which can be used on this machine to connect to the network.
         | Unless otherwise specified (by system property or command-line switch), the first proxy
         | specification in this list marked as active will be used.
         |-->
        <proxies>
          <proxy>
          <id>optional</id>
          <active>true</active>
          <protocol>http</protocol>
          <!--      <username>prayag</username>
                    <password></password>
          -->
          <host>10.**.***.**5</host>
          <port>8080</port>
          <nonProxyHosts>google.com|github.com</nonProxyHosts>
          </proxy>
        </proxies>

    </settings>


## [play with cascalog cli](http://cascalog.org/articles/getting_started.html)

```
prayagupd@prayagupd:~/backup/hacker_/nepleaks$ lein repl
user=> (use 'cascalog.api)
nil
user=> (use 'cascalog.playground)
nil
user=> sentence
[["Four score and seven years ago our fathers brought forth on this continent a new nation"] ["conceived in Liberty and dedicated to the proposition that all men are created equal"] ["Now we are engaged in a great civil war testing whether that nation or any nation so"] ["conceived and so dedicated can long endure We are met on a great battlefield of that war"] ["We have come to dedicate a portion of that field as a final resting place for those who"] ["here gave their lives that that nation might live It is altogether fitting and proper"] ["that we should do this"] ["But in a larger sense we can not dedicate  we can not consecrate  we can not hallow"] ["this ground The brave men living and dead who struggled here have consecrated it"] ["far above our poor power to add or detract The world will little note nor long remember"] ["what we say here but it can never forget what they did here It is for us the living rather"] ["to be dedicated here to the unfinished work which they who fought here have thus far so nobly"] ["advanced It is rather for us to be here dedicated to the great task remaining before us "] ["that from these honored dead we take increased devotion to that cause for which they gave"] ["the last full measure of devotion  that we here highly resolve that these dead shall"] ["not have died in vain  that this nation under God shall have a new birth of freedom"] ["and that government of the people by the people for the people shall not perish"] ["from the earth"]]

user=> (?- (stdout) sentence)
14/02/13 11:19:09 INFO util.HadoopUtil: using default application jar, may cause class not found exceptions on the cluster
14/02/13 11:19:09 INFO planner.HadoopPlanner: using application jar: /home/pupadhyay/.m2/repository/cascading/cascading-hadoop/2.2.0/cascading-hadoop-2.2.0.jar
14/02/13 11:19:09 INFO property.AppProps: using app.id: 66FFB8A741E1485382DD1793F1630A36
14/02/13 11:19:10 INFO util.Version: Concurrent, Inc - Cascading 2.2.0
14/02/13 11:19:10 INFO flow.Flow: [] starting
14/02/13 11:19:10 INFO flow.Flow: []  source: MemorySourceTap["MemorySourceScheme[[UNKNOWN]->[ALL]]"]["/7d78e7f9-3546-497a-83fb-9cdbcd7f1cd6"]
14/02/13 11:19:10 INFO flow.Flow: []  sink: StdoutTap["SequenceFile[[UNKNOWN]->[ALL]]"]["/tmp/temp78507057347127259497865011123323"]
14/02/13 11:19:10 INFO flow.Flow: []  parallel execution is enabled: false
14/02/13 11:19:10 INFO flow.Flow: []  starting jobs: 1
14/02/13 11:19:10 INFO flow.Flow: []  allocating threads: 1
14/02/13 11:19:10 INFO flow.FlowStep: [] starting step: (1/1) ...7347127259497865011123323
14/02/13 11:19:11 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
14/02/13 11:19:11 INFO flow.FlowStep: [] submitted hadoop job: job_local_0001
14/02/13 11:19:11 INFO util.ProcessTree: setsid exited with exit code 0
14/02/13 11:19:12 INFO mapred.Task:  Using ResourceCalculatorPlugin : org.apache.hadoop.util.LinuxResourceCalculatorPlugin@be630d4
14/02/13 11:19:12 INFO mapred.MapTask: numReduceTasks: 0
14/02/13 11:19:12 INFO hadoop.FlowMapper: cascading version: 2.2.0
14/02/13 11:19:12 INFO hadoop.FlowMapper: child jvm opts: -Xmx200m
14/02/13 11:19:12 INFO hadoop.FlowMapper: sourcing from: MemorySourceTap["MemorySourceScheme[[UNKNOWN]->[ALL]]"]["/7d78e7f9-3546-497a-83fb-9cdbcd7f1cd6"]
14/02/13 11:19:12 INFO hadoop.FlowMapper: sinking to: StdoutTap["SequenceFile[[UNKNOWN]->[ALL]]"]["/tmp/temp78507057347127259497865011123323"]
14/02/13 11:19:12 INFO mapred.Task: Task:attempt_local_0001_m_000000_0 is done. And is in the process of commiting
14/02/13 11:19:12 INFO mapred.LocalJobRunner: 
14/02/13 11:19:12 INFO mapred.Task: Task attempt_local_0001_m_000000_0 is allowed to commit now
14/02/13 11:19:12 INFO mapred.FileOutputCommitter: Saved output of task 'attempt_local_0001_m_000000_0' to file:/tmp/temp78507057347127259497865011123323
14/02/13 11:19:12 INFO mapred.LocalJobRunner: 
14/02/13 11:19:12 INFO mapred.Task: Task 'attempt_local_0001_m_000000_0' done.
14/02/13 11:19:12 INFO mapred.FileInputFormat: Total input paths to process : 1
14/02/13 11:19:12 INFO util.Hadoop18TapUtil: deleting temp path /tmp/temp78507057347127259497865011123323/_temporary
nil


RESULTS
-----------------------
Four score and seven years ago our fathers brought forth on this continent a new nation
conceived in Liberty and dedicated to the proposition that all men are created equal
Now we are engaged in a great civil war testing whether that nation or any nation so
conceived and so dedicated can long endure We are met on a great battlefield of that war
We have come to dedicate a portion of that field as a final resting place for those who
here gave their lives that that nation might live It is altogether fitting and proper
that we should do this
But in a larger sense we can not dedicate  we can not consecrate  we can not hallow
this ground The brave men living and dead who struggled here have consecrated it
far above our poor power to add or detract The world will little note nor long remember
what we say here but it can never forget what they did here It is for us the living rather
to be dedicated here to the unfinished work which they who fought here have thus far so nobly
advanced It is rather for us to be here dedicated to the great task remaining before us 
that from these honored dead we take increased devotion to that cause for which they gave
the last full measure of devotion  that we here highly resolve that these dead shall
not have died in vain  that this nation under God shall have a new birth of freedom
and that government of the people by the people for the people shall not perish
from the earth
-----------------------
user=> 

```


## run webapp

To start a web server for the application, run:

    lein ring server 8443

## License

Copyright © 2013 pseudononymous-upd
