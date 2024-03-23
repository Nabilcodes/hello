### COMMIT 1 REFLECTION NOTES

In this particular section of my work, I learnt how to assemble a simple rust program
that may handle an incoming TCP requests and try to display the message. While learning
how to display the message, I also learn some use cases of how I may use the vector and 
some standard library in rust, like net and input output. I also learnt more about the 
concept of traits and its practical use. Furthermore, I also deepen my networking knowledge
about the difference of the concept of streams and connection.

### COMMIT 2 REFLECTION NOTES

There was some addition to the function handle_connection, which was

1. A response variable that holds the success message’s data. he write_all method on stream takes a &[u8] and sends those bytes directly down the connection.Because the write_all operation could fail, we use unwrap on any error result.
2. Added fs to the use statement to bring the standard library’s filesystem module into scope.
3. Used format! to add the file’s contents as the body of the success response. To ensure a valid HTTP response, we add the Content-Length header which is set to the size of our response body, in this case the size of hello.html.

![image](https://github.com/Nabilcodes/hello/assets/71275597/800a45b1-ea18-4634-a48d-e4a37b7445d9)

### COMMIT 3 REFLECTION NOTES

> How to split between response

1. Check the content of the request (added request_line, obtained using buf_reader)
2. Make an if-else block (if the request was GET HTTP/1.1 proceed as usual returning status line 200 OK, otherwise return 404.html with status line 404 NOT FOUND"

> Why refactoring step was needed

There are a lot of repetition takes place : reading files and writing contents.
Refactoring was made by only determining the calue fo the status line and file name in the if else block.

![image](https://github.com/Nabilcodes/hello/assets/71275597/f7bc132a-966c-416b-b49f-439efd8ffe9d)

### COMMIT 4 REFLECTION NOTES

now the request handling was done using match.
if the endpoint /sleep was called, sleep would occur before returning hello.html.

### COMMIT 5 REFLECTION NOTES

> How a thread pool works

a thread pool is used to hold a finite number of thread.

threadpool can be used in practical purpose as opposed to the idea of spawning up to infinite number of thread which is prone to DoS attack.

An implementation of a threadpool may be written in another file, for example a rust file named lib.
we can then import the threadpool via use in the main file.

A threadpool implementation may consist of the function new and execute, corresponding to the implementation of thread::spawn.

in the new() method, we obviously need some structure to store the threads we're going to make.

in this implementation, we don't directly uses thread, but it was wrapped by a newly introduced data structure named Worker thath serve as a waiter for the code which execute it till the end.
The storage for the threads then become the storage for the workers. Let's call this structure Workers.

next thing to do was implementing sender and receiver mechanism using the library mpsc. because some workers may need to own a single receiver, we need to add the type arc and mutual exclusion (Mutex) to 
make sure that at one particular time, one worker will only get one job.




