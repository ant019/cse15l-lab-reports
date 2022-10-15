# Lab Report 3

## Part 1 - Search Engine
For this part of the lab, I developed a simple search engine that adds to its own library for it to search through from lab 2.
This is the code that I made for the engine down below:

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Search implements URLHandler{
    ArrayList<String> searchResults = new ArrayList<String>();
    @Override
    public String handleRequest(URI url){
            if (url.getPath().contains("add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    searchResults.add(parameters[1]);
                    return String.format("%s", searchResults);
                }
            }
            else if(url.getPath().contains("search")){
                // String search = url.substring((url.indexOf("=")));
                ArrayList<String> list = new ArrayList<String>();
                String[] search = url.getQuery().split("=");
                if (search[0].equals("s")) {
                    //add for loop
                    for(int i = 0; i<searchResults.size();i++){
                        if(searchResults.get(i).contains(search[1])){
                            list.add(searchResults.get(i));
                        }                
                    }
                    return String.format("%s", list);
                }                        
            }
            else{
                return String.format("%s", searchResults);
            }
        
        return "404 Not Found!";
    }
}

class SearchServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Search());
    }
}
```

There are two methods that are in this code that rely on the url. First off, we have the add method, where
if the term "add" is found in the url, it splits off the url from before and after the equals sign, starting at the query,
into an array called parameters. If the first element of this array is "s", then the second element of the array gets added
into the searchResults array. Here are some examples of the add method being used.

### Add method:

![image](https://user-images.githubusercontent.com/114563712/195968274-b24e18d4-f949-481a-92d1-d86f0977b410.png)

![image](https://user-images.githubusercontent.com/114563712/195968408-45f0d443-d0b7-4a93-9baf-19aa10d56221.png)

In the second image here, we refreshed the page a couple of times to get the word "apple" repeating a few times over.
Everytime the user hits enter with a url like `http://localhost:12345/add?s=apple` the term "apple" would be added
to the array.

The next method that rely on the url is the search method. This works similarly to the add method in the sense that
the url gets split to before and after the equal sign, starting at the query; however, in place of the word "add"
in the url, the code looks for the word "search". If the first element of the parameters array is "s",
then the second element of the array is what is used to search through the searchResults array. 
Here is an example of the search method being used.

### Search method:
![image](https://user-images.githubusercontent.com/114563712/195968778-23c1c8b3-e8fb-4018-b4f1-cdcbcc2e13ee.png)

![image](https://user-images.githubusercontent.com/114563712/195968879-d9c07e21-3a5d-471b-b46a-85c7e0b29611.png)

Using the list from before, for the first image, we searched for the term "apple" and showed up all the results that 
contain a sequence of strings in the form of "apple". For the second image, we search for the term "og" and all the 
results that showed up were the words that had "og" in them.

### Default page:
![image](https://user-images.githubusercontent.com/114563712/195968534-9de14ad1-9df5-4666-8938-f741f43cc533.png)

This is just the page that you end up at if you do not have "add" or "search" in your url. This prompts you to type
`"/add?s=[input]"` to add or `"/search?s=[input]"` 

## Part 2 - Buggy Files
The two files with bugs that I am choosing to report about are ArrayExamples.java and ListExamples.java.
More specifically, I will be discussing the bugs in the averageWithoutLowest method and the filter method. 

### Bug 1 - averageWithoutLowest()
The comment for the averageWithoutLowest method is as follows:
```
   Averages the numbers in the array (takes the mean), but leaves out the
   lowest number when calculating. Returns 0 if there are no elements or just
   1 element in the array
```
#### Failure-Inducing Input
```
  @Test
  public void averageWithoutLowest(){
    double[] testArray = {8, 5, 7, 2, 2};
    double expected = 22.0/4.0;
    assertEquals(expected,ArrayExamples.averageWithoutLowest(testArray), 0.1);
  }
```

#### Symptom
![image](https://user-images.githubusercontent.com/114563712/195969554-abbe3288-fce2-454f-9a8e-b37dc839d5f5.png)


#### The Fix
##### Original Code:
```
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```
##### Code Revision:
```
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      sum += num;
    }
    sum-=lowest;
    return sum / (arr.length - 1);
  }
```

#### Explanation
In the original code of this method, the code would leave out all of the lowest numbers if there were multiple.
So in order to fix this, I removed the if statement that checked if the number was the lowest, and added all of 
numbers in the list anyway. Then to account for the lowest number, I subtracted it by one of the lowest numbers
right before the return statement that actually averages the sum of the numbers.

### Bug 2
The comment for the filter method is as follows:
```
   Returns a new list that has all the elements of the input list for which
   the StringChecker returns true, and not the elements that return false, in
   the same order they appeared in the input list;
```

#### Failure-Inducing Input
```
    @Test
    public void filter(){
        List<String> testList = new ArrayList<>();
        testList.add("baseball");
        testList.add("volleyball");
        testList.add("soccer");
        List<String> expected = new ArrayList<>();
        expected.add("baseball");
        expected.add("volleyball");
        StringChecker s = new Checker();
        assertEquals(expected,ListExamples.filter(testList,s));
    }
```

#### Symptom
![image](https://user-images.githubusercontent.com/114563712/195969577-83653146-d303-42dd-8100-d90d3d50a142.png)


#### The Fix
##### Original Code:
```
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }
```
##### Code Revision:
```
class Checker implements StringChecker{
  public boolean checkString(String s){
    if(s.length()>6){
      return true;
    }
    return false;
  }
}
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }
```
#### Explanation
Initially, the original code did not have a class to implement the StringChecker interface, so it
never had the checkString method. After writing the method the other most notable symptom was that
the method was adding the elements in an incorrect order. This was caused by the line `result.add(0, s)`,
which would add the most recent element to the 0 index or beginning of the list.

# This Concludes The Lab!
