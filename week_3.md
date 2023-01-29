# Lab Report 2

## Part 1
### StringServer Code:
~~~
import java.io.IOException;
import java.net.URI;

class Handler3 implements URLHandler {
    String runningString = new String();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return runningString;
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    runningString += "\n" + parameters[1];
                    return runningString;
                }
            }
        }
        return "404 Not Found!";

    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler3());
    }
}
~~~~
*Created using code from Lab 2 as a base*

### /add-message Examples:
![Image](https://github.com/ryanliulwy/cse15l-lab-reports/blob/main/screenshots/hello_output.png)
- The method handleRequest() is called, which then calls getPath(), contains(), getQuery(), split(), and equals()
  - handleRequest() takes in a full url as an argument
    - In this case it would be https://localhost:4000/add-message?s=Hello
  - getPath() is used to isolate the url path
    - In this case it returns "/add-message?s=Hello"
  - contains() takes in a specific string as an argument and returns true if the argument string is found in the calling string
    - In this case we are looking for "/add-message"
  - getQuery() returns the portion of the path after the "?"; in this case it returns "s=Hello"
- The String variable runningString is the data field changed as a result of this request

![Image](https://github.com/ryanliulwy/cse15l-lab-reports/blob/main/screenshots/how_are_you_output.png)


## Part 2


## Part 3
