#19th
docker build -t java-app .
docker run -d -t java-app

17th docker volume and 15

docker --version
docker ps
docker ps -a
docker images
docker run myfirstimage:latest
docker pull nginx
docker run -d -p 8081:80 nginx
docker ps
docker stop <container_id>
docker rm <container_id>

docker volume create myvolume
docker volume create dvolume
docker volume ls
docker run -it -v myvolume:/data ubuntu bash
cd data
echo "Docker Volume Persistence Test" > test.txt
exit
docker run -it -v myvolume:/data ubuntu bash
cat/data/test.txt
cat /data/test.txt
exit
docker run -d -p 8086:80 -v myvolume:/usr/share/nginx/html nginx
docker run -it -v myvolume:/data ubuntu bash
echo "<h1>Persistent Web Page</h1>" /data/index.html
exit
docker run -d -p 8083:80 -v myvolume:/usr/share/nginx/html nginx
docker run -it -v myvolume:/data ubuntu bash
echo "<h1>Persistent Web Page</h1>" /data/index.html


16th docer image using docker file
main FOlder
Sample.java - Print("Hello from Docker")
Dockerfile 

FROM eclipse-temurin:17-jdk
WORKDIR /app
COPY . /app
RUN javac Sample.java
CMD ["java","Sample"]

docker build -t java-image .
docker run java-image
docker images
docker ps -a


12th mvn
mvn archetype:generate
mvn package (T2)

package bnmit.org;

public class Calculator {

    public int add(int a, int b){
        return a + b;
    }

    public int sub(int a, int b){
        return a - b;
    }

    public int multiply(int a, int b){
        return a * b;
    }

    public int div(int a, int b){
        return a / b;
    }
}

Test:
package bnmit.org;

import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class CalculatorTest {

    Calculator calc = new Calculator();

    @Test
    void testAdd() {
        assertEquals(5, calc.add(2, 3));
    }

    @Test
    void testSub() {
        assertEquals(1, calc.sub(3, 2));
    }

    @Test
    void testMultiply() {
        assertEquals(6, calc.multiply(2, 3));
    }

    @Test
    void testDiv() {
        assertEquals(2, calc.div(6, 3));
    }

    @Test
    void testDivByZero() {
        assertThrows(ArithmeticException.class, () -> calc.div(5, 0));
    }
}
mvn clean test (t1)

18th docker push

docker images
docker login
docker tag <image> <username>/<repository-name>
docker images
docker pull <username>/<repository-name>
docker pull <username>/<repository-name>




1.#highest number max .java
class MaxInput {

    public static int findMax(int a, int b, int c) {
        int max = a;
        if (b > max) max = b;
        if (c > max) max = c;
        return max;
    }
}
1.#highest number junit
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class MaxInputTest {

    @Test
    void testMax1() {
        assertEquals(30, MaxInput.findMax(10, 30, 20));
    }

    @Test
    void testMax2() {
        assertEquals(50, MaxInput.findMax(50, 10, 20));
    }

    @Test
    void testMax3() {
        assertEquals(40, MaxInput.findMax(10, 20, 40));
    }
}

pom xml file to get jacaco
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.bnmit</groupId>
    <artifactId>com.bnmit</artifactId>
    <version>1.0-SNAPSHOT</version>

    <name>com.bnmit</name>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.release>17</maven.compiler.release>
    </properties>

    <!-- JUnit BOM -->
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.junit</groupId>
                <artifactId>junit-bom</artifactId>
                <version>5.11.0</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>

    <!-- Dependencies -->
    <dependencies>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <!-- Build -->
    <build>
        <plugins>

            <!-- Compiler -->
            <plugin>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.13.0</version>
            </plugin>

            <!-- Run JUnit 5 -->
            <plugin>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>3.3.0</version>
            </plugin>

            <!-- JaCoCo Plugin -->
            <plugin>
                <groupId>org.jacoco</groupId>
                <artifactId>jacoco-maven-plugin</artifactId>
                <version>0.8.11</version>

                <executions>
                    <!-- Attach agent -->
                    <execution>
                        <goals>
                            <goal>prepare-agent</goal>
                        </goals>
                    </execution>

                    <!-- Generate coverage report -->
                    <execution>
                        <id>report</id>
                        <phase>test</phase>
                        <goals>
                            <goal>report</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>

        </plugins>
    </build>

</project>
