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
