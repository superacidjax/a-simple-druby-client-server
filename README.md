#A simple dRuby Client/Server

###Instructions

You'll need two separate terminal windows.

In terminal 1, run the following to start the server:
```
ruby puts00.rb druby://localhost:12345
```

In terminal 2, run the following to run the client:

```
ruby hello00.rb druby://localhost:12345
```

**You should see the output "Hello World" in the terminal 1 server window.**

####Welcome to dRuby!

##The code explained

###The Server

In ```puts00.rb```

First, we require the drb library. Then, we create a class that contains the method we're going to make available to the client(s) of the service.

```DRb.start_service(uri, Puts.new)``` starts the dRuby service, it requires a URI which would be passed in from the user, and it instantiates an instance of the ```Puts``` class.

The final line is very important because a dRuby service runs on a separate thread. ```DRb.thread.join()``` ensures the program stays running after it has initially executed -- otherwise, it would just stop. This line "keeps the server running" -- effectively.

###The Client

The client is extremely simple.

You pass a URI when you start the program like this:

```
ruby hello00.rb druby://localhost:12345
``` 

That URI is required for creating the new DRb object. Once the client is connected, it simply calls ```puts``` on the string which, in this case is ```Hello World```.

---

Not much to it!
