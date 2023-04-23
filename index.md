# Lab Report 2

Part 1:
In this part of the lab report, I had to write a web server called StringServer that could concatenate messages written by the user. The query would be writen in the url of the website and that would be printed out on the website alongside previous messages. The code that I used to make this program is in the screenshot below 

![Image](StringServerCode.png)

There are a couple of methods in my code that are called to make it work properly, more specfically I run handleRequest, handle, and start. The purpose of handleRequest is to take the information given in the url of the server and use it to return the message. The relevant arguements in this method the given url since with that url there is a array called paramters that locates the query and adds and returns the correct message. The string message is a changing and relevant field in the class since it changes whenever the url of the website changes and includes the right query. In addition, paramters is another field that is changing within the program. The next method I use is handle which is located in the Server class. The purpose of this code is to take the return statement after being handled by the code and then to write it onto the browser. The parameter exchange is a relevent argument to this method that is also changing as more messages are written on the web server. The final method that is called is start which creates a request entrypoint and starts the server. There are two arguements in this method, port and handler. The parameters don't change while the program is running because once the server starts it doesn't stop until the user closes the program and the port number doesn't change while the program is being run. 

The implementation of this method is shown in the next two screenshots where messages are being added. 
![Image](Message1.png)
![Image](Message2.png)

Part 2:

In the code given as a part of lab 3, there were plenty of methods that had bugs in them. I chose to examine the reverseInPlace method in ArrayExamples.java. A failure-inducing input for the buggy program is provides in the code written below. 

```json

public void testReverseInPlace() {
    int[] input1 = { 1, 2, 3 , 4, 5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5, 4, 3, 2, 1 }, input1);
	}

```

The result of this program would be {5, 4, 3, 4, 5}. However, this code can work for certain inputs. The following code is an example:
```json

public void testReverseInPlace2() {
    int[] input1 = {1};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{1 }, input1);
	}

```
The symptom, as the output of running the tests is shown in the screenshot below:
![Image](JUnitTestOutput.png)

In order to fix this problem I had to edit the method to properlly run store the entire list. The incorrect code is first provided and then the correct code is given. 

```json

static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }

```

```json

static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i = i+ 1) {
        int temp = arr[i];
        arr[i] =  arr[arr.length - i - 1];
        arr[arr.length - i - 1] = temp;

    }
  }

```

The reason why the second code is correct is because the first code doesn't have a temporary holder for value and thus for later values in the array the new arr[i] is different from the index it is supposed to be accessing. Thus, the second code doesn't even iterate through those values in the for loop and instead uses an temp variable to store the element in a spot that won't get modified. 

Part 3:
I have learned a lot in the labs but one thing in particular that I didn't know before was how to create a web server. It was very interesting to see how something as common as a website was developed. I enjoyed the many methods that it look to get simple text on the screen. I also didn't know much about the different components of a url. 




