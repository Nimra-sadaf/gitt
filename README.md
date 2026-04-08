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
