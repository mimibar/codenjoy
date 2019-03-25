To configure the client, do the following:
* DotNet client
    - read src\main\dotNet\Readme.txt
* Python client
    - read src\main\dotNet\README.MD
    - read src\main\dotNet\README.MD
* JS client
    - read src\main\javascript\README.txt
* Java client
    - install Java (JDK 7 or 8)
    - install Maven3
    - import the current project as a Maven project into Intellij Idea (Eclipse is not recommended)
    - if there is no internet and engine dependency will not suffice
        = on the page http://host/codenjoy-contest/help you can download the zip with this dependency
            ~ here is host
                = server_ip:8080 for playing with the server raised on the local network
                = codenjoy.com to play with a shared server hosted on the Internet
        = there are also instructions for the game
    - in class .\src\main\java\com\codenjoy\dojo\<game_package>\client\YourSolver.java
        = enter the email with which you registered on the server in the constant USER_NAME
        = write your logic in the method
            public String get(Board board) {
        = run YourSolver class as main method
            ~ note that for a game with a local server in the main method, you should uncomment the line
                WebSocketRunner.runOnServer("192.168.1.1:8080", // to use for local server
            ~ specify server IP
            ~ and comment out the line for connecting to a remote server
                WebSocketRunner.run(WebSocketRunner.Host.REMOTE, // to use for codenjoy.com server
        = Check out http://host/codenjoy-contest/board/game/<game_name>
          your bot was supposed to start moving
        = restart the process if you made changes
            ~ attention! only one YourSolver can be launched at a time - watch it
    - in class .\src\main\java\com\codenjoy\dojo\<game_package>\client\Board.java
        = you can complement the help methods for parsing boards from the string
    - In the test package .\src\test\java\com\codenjoy\dojo\<game_package>\client
        = you can post your tests
    - Codenjoy!