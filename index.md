Name: Hargen Zheng
PID: A17383701
Sources: Week 2 Lab 'NumberServer.java', 'Handler.class', ad 'URLHandler.class' files.
Lab Session: Wednesday 11:00 - 12:50 @EBU3B_B270

# Lab Report 2 
Welcome to my lab report 2 webpage. In this lab report, I have included the details of my implementation to create a simple web server called StringServer; description of bug fixes from the Week 3 lab; and a reflection of what I have learned from previous two weeks of labs. Let's first dive into the first part -- creating a web server from "scratch."

# Part 1: Web server: StringServer

> My code Implementation
```ruby
import java.io.IOException;
import java.net.URI;
import java.lang.StringBuilder;

class Handler implements URLHandler {
    StringBuilder str = new StringBuilder();
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("%s", str);
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    StringBuilder result = new StringBuilder();
                    for(int i = 1; i < parameters.length; i++){
                        result.append(parameters[i]);
                    }
                    str.append(result + "\n");
                    return String.format("%s is added! It's now visible", result); 
                }
                return null; 
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

        Server.start(port, new Handler());
    }
}

```
