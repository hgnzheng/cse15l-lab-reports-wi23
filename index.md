Name: Hargen Zheng
PID: A17383701
Lab Session: Wednesday 11:00 - 12:50 @EBU3B_B270

# Lab Report 2 

# Part 1: Web server: StringServer

```
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
