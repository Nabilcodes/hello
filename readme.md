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