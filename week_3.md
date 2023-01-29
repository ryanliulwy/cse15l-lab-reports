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
  - getQuery() returns the portion of the path after the "?"
    - In this case it returns "s=Hello"
  - split() identifies the expression used to separate the paramenters passed in the query
    - Here we use "=" to split the query
  - equals() compares if the calling string and the input string are the same
    - Here we use it to make sure the first parameter in the query is "s"
- The String variable runningString is the data field changed as a result of this request
    - runningString is currently an empty string
    - "\nHello" is added to runningString
    - runningString now contains "\nHello"

![Image](https://github.com/ryanliulwy/cse15l-lab-reports/blob/main/screenshots/how_are_you_output.png)

Pretty much the same as above, with a few differences in specific inputs
- The method handleRequest() is once again called, which still calls getPath(), contains(), getQuery(), split(), and equals()
  - handleRequest() takes in a full url as an argument
    - In this case it would be https://localhost:4000/add-message?s= **How are you**
  - getPath() is used to isolate the url path
    - In this case it returns "/add-message?s=**How are you**"
  - contains() takes in a specific string as an argument and returns true if the argument string is found in the calling string
    - We are still looking for "/add-message"
  - getQuery() returns the portion of the path after the "?"
    - In this case it returns "s=**How are you**"
  - split() identifies the expression used to separate the paramenters passed in the query
    - We still use "=" to split the query
  - equals() compares if the calling string and the input string are the same
    - We still want the first parameter to be "s"
- The String variable runningString is the data field changed as a result of this request
    - runningString currently contains "\nHello"
    - "\nHow are you" is added to runningString
    - runningString now contains "\nHello\nHow are you"


## Part 2
Testing original ArrayExamples reversed method
### Failure-inducing input
    @Test
    public void testReversedThreeElements() {
        int[] input2 = {1, 2, 3};
        assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reversed(input2));
    }
### Non-failure-inducing input
    @Test
    public void testReversedEmpty() {
        int[] input1 = { };
        assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
    }
### Symptom
![Image](https://github.com/ryanliulwy/cse15l-lab-reports/blob/main/screenshots/reversed_symptom.png)
### Bug fix
Original code:

    static int[] reversed(int[] arr) {
        int[] newArray = new int[arr.length];
        for(int i = 0; i < arr.length; i += 1) {
            arr[i] = newArray[arr.length - i - 1];
        }
        return arr;
    }

Fixed code:

    static int[] reversed(int[] arr) {
        int[] newArray = new int[arr.length];
        for(int i = 0; i < arr.length; i += 1) {
            newArray[arr.length - i - 1] = arr[i];
        }
        return newArray;
    }

The bug was. To fix this,

## Part 3
I learned a lot about paths and urls during week 2, such as the names and purpose of different parts in a url (domain, path, query). During lab, I was able to put this into practice by creating and hosting my own basic search engine website locally with localhost, another skill that I did not have before. I was also able to try hosting the same website on the ieng6 server, and it was cool seeing how my lab partner could send requests through his computer that would then be reflected on mine.
