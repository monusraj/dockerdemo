1) Create a java file which print "Hello, World"

cat HelloWorld.java

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World");
    }
}

2) Compile file using javac which will generate HelloWorld.class

#yum install java-devel

javac HelloWorld.java

You can test output using java command.

[root@ansible]# java HelloWorld
Hello, World


3) Create a Dockerfile, which will add java.class and jre in container

FROM alpine:latest
ADD HelloWorld.class HelloWorld.class
RUN apk --update add openjdk8-jre
ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "HelloWorld"]

4) Create Docker Hello World Image and Run it

$ docker build --tag "docker-hello-world:latest" .

5) 

$ docker run docker-hello-world:latest

