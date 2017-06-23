# Akka Quickstart with Java
 
Akka is a toolkit and runtime for building highly concurrent, distributed, and fault-tolerant event-driven applications on the JVM. Akka can be used with both Java and Scala.
This guide introduces Akka by describing the Java version of the Hello World example. If you prefer to use Akka with Scala, switch to the [Akka Quickstart with Scala guide](http://developer.lightbend.com/guides/akka-quickstart-scala/). 

Actors are the unit of execution in Akka. The Actor model is an abstraction that makes it easier to write correct concurrent, parallel and distributed systems. The Hello World example illustrates Akka basics. Within 30 minutes, you should be able to download and run the example and use this guide to understand how the example is constructed. This will get your feet wet, and hopefully inspire you to dive deeper into the wonderful sea of Akka!

After trying this example the comprehensive [Getting Started Guide](http://doc.akka.io/docs/akka/2.5/java/guide/introduction.html) is a good next step to continue learning more about Akka.

## Downloading the example 

The Hello World example for Java is a zipped project that includes a build files for Maven and Gradle. You can run it on Linux, MacOS, or Windows. The only prerequisite is Java 8 and an installation of [Maven](https://maven.apache.org) or [Gradle](https://gradle.org).

Download and unzip the example:

1. Download the zip file from [Lightbend Tech Hub](http://dev.lightbend.com/start/?group=akka&project=akka-quickstart-java) by clicking `CREATE A PROJECT FOR ME`. 
1. Extract the zip file to a convenient location: 
  - On Linux and OSX systems, open a terminal and use the command `unzip akka-quickstart-java.zip`.
  - On Windows, use a tool such as File Explorer to extract the project. 

## Running the example

Make sure that you have installed the build tool of your choice and thereafter open a Terminal window and, from inside the project directory, type the following to run Hello World:

Maven
:   
```
$ mvn compile exec:exec
```

Gradle
:   
```
$ gradle run
```

The output should look _something_ like this (scroll all the way to the right to see the Actor output):
 
Maven
: ```
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building app 1.0
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] --- exec-maven-plugin:1.6.0:exec (default-cli) @ app ---
>>> Press ENTER to exit <<<
[INFO] [05/11/2017 14:07:20.790] [helloakka-akka.actor.default-dispatcher-2] [akka://helloakka/user/printerActor] Hello, Java
[INFO] [05/11/2017 14:07:20.791] [helloakka-akka.actor.default-dispatcher-2] [akka://helloakka/user/printerActor] Good day, Play
[INFO] [05/11/2017 14:07:20.791] [helloakka-akka.actor.default-dispatcher-2] [akka://helloakka/user/printerActor] Howdy, Akka
[INFO] [05/11/2017 14:07:20.791] [helloakka-akka.actor.default-dispatcher-2] [akka://helloakka/user/printerActor] Howdy, Lightbend
```

Gradle
: ```
:compileJava UP-TO-DATE
:processResources NO-SOURCE
:classes UP-TO-DATE
:run
>>> Press ENTER to exit <<<
[INFO] [05/11/2017 14:08:22.884] [helloakka-akka.actor.default-dispatcher-2] [akka://helloakka/user/printerActor] Howdy, Akka
[INFO] [05/11/2017 14:08:22.884] [helloakka-akka.actor.default-dispatcher-2] [akka://helloakka/user/printerActor] Good day, Play
[INFO] [05/11/2017 14:08:22.884] [helloakka-akka.actor.default-dispatcher-2] [akka://helloakka/user/printerActor] Hello, Java
[INFO] [05/11/2017 14:08:22.884] [helloakka-akka.actor.default-dispatcher-2] [akka://helloakka/user/printerActor] Howdy, Lightbend
<=========----> 75% EXECUTING
> :run
```
   
Congratulations, you just ran your first Akka app. Now take a look at what happened under the covers. 

## What Hello World does

As you saw in the console output, the example outputs several greetings. Let’s take a look what happens at runtime.

![Architecture](images/hello-akka-architecture.png)

First, the `main` class creates an `akka.actor.ActorSystem`, a container in which Actors run. Next, it creates three instances of a Greeter Actor and one instance of a Printer Actor. 

The example then sends messages to the Greeter Actor instances, which store them internally. Finally, instruction messages to the Greeter Actors trigger them to send messages to the Printer Actor, which outputs them to the console:

![Messages](images/hello-akka-messages.png)

Akka's use of Actors and asynchronous messaging result in a range of benefits. Consider a few.

## Benefits of using the Actor Model

The following characteristics of Akka allow you to solve difficult concurrency and scalability challenges in an intuitive way: 

* Event-driven model &#8212; Actors perform work in response to messages. Communication between Actors is asynchronous, allowing Actors to send messages and continue their own work without blocking to wait for a reply.
* Strong isolation principles &#8212; Unlike regular objects in Java, an Actor does not have a public API in terms of methods that you can invoke. Instead, its public API is defined through messages that the actor handles. This prevents any sharing of state between Actors; the only way to observe another actor's state is by sending it a message asking for it.
* Location transparency &#8212; The system constructs Actors from a factory and returns references to the instances. Because location doesn't matter, Actor instances can start, stop, move, and restart to scale up and down as well as recover from unexpected failures. 
* Lightweight &#8212; Each instance consumes only a few hundred bytes, which realistically allows millions of concurrent Actors to exist in a single application.
 
Let's look at some best practices for working with Actors and messages in the context of the Hello World example.

@@@index

* [Define the Actors and messages](define-actors.md)
* [Create the Actors](create-actors.md)
* [Communicate with Actors](communicate-with-actors.md)
* [The Main Class](main-class.md)
* [Full Example](full-example.md)
* [Testing Actors](testing-actors.md)
* [Running the Application](running-the-application.md)
* [IntelliJ](intellij-idea.md)

@@@
