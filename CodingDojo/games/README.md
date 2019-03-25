Create your Codenjoy game
==============

Introduction
--------------
[Codenjoy](http://codenjoy.com) is a CodingDojo framework for developers. The purpose of his fun'ovye
team building activities and / or coding training.
Already [there are a number of games on board](http://codenjoy.com/codenjoy-contest).
And you can write another one of your own.

Setting the development environment
--------------
All you need to develop the game is jdk7, maven3, git-client and IDE Idea.

- install yourself a git client, for example [tortoise git](https://code.google.com/p/tortoisegit/)
- register yourself an account on [github](http://github.com) or [bitbucket](http://bitbucket.org)
- make a fork (or just a copy of the sample project) from the [current repository](https://github.com/codenjoyme/codenjoy-game)
- then pull the project to the computer
- install [maven3](https://maven.apache.org/download.cgi) (download the archive and unpack it in `c:\java`)
- write the environment variable `M2_HOME`, pointing to the root of the`c:\java\apache-maven-3.x.x` folder
- add the line `;%M2_HOME%\bin` to the end of the `Path` variable
- install jdk7 if not installed (also in the folder `c:\java`)
- write the environment variable `JAVA_HOME`, pointing to the root of the`c:\java\jdk1.8.x_xx` folder
- add the line `;%JAVA_HOME%\bin` to the end of the Path variable
- check that everything is done correctly by running cmd.exe and in it the command `mvn -version`.
If it is installed, you will see the output of the command: the version of maven and java, and not that "command not found"
```
C:\Users\user>mvn -version
Apache Maven 3.x.x
Maven home: C:\java\apache-maven-3.x.x
Java version: 1.8.x_x, vendor: Oracle Corporation
Java home: C:\java\jdk1.8.x_xx\jre
Default locale: xxxxx, platform encoding: xxxxxxx
OS name: "xxxxxxxxxx", version: "xxx", arch: "xxxxx", family: "xxxxxxx"
C:\Users\user>
```
- download and install [IntelliJ IDEA Community version](https://www.jetbrains.com/idea/download/)

Codenjoy engine installation
--------------

For normal operation, you need to install the dependency `engine`. She is located
in the same folder `engine`. Be careful, its version may change and you will have to
update both her and the sources of your game. For this:

- go to the 'engine' folder
- run 'setup.bat'
- make sure that everything is established successfully - the dependency should be
installed in `C:\Users\<Твой_юзер>\.m2\repository\com\codenjoy\engine`

Game work
--------------

Think up / remember a game that would be interesting (but not complicated by the rules) and
familiar to all from childhood. The game may be identical to the original by the rules, and may
and differ from the original to a greater or lesser extent. For example - in the sea battle usually
play two, but you can realize the sea battle for an unlimited number of players.
It is worth checking here that writing the AI ​​algorithm was interesting for the player (not very easy
and not very difficult). Feel free to [write to us](http://codenjoy.com/portal/?page_id=51)
if you are at a loss with the choice - we will help.

After that, start writing the model of your chosen game. The next section describes in detail
how to do it. [Here is an example](http://apofig.blogspot.com/2011/10/9-tdd.html) of how
written model snake. It is very desirable that it be covered with unit tests.
Even better, the code was written on TDD, if you do not know how [watch this video](https://vimeo.com/54862036)
and then write to us. Code review if necessary organize. And after modelka
will be ready to integrate it into our framework and help with the organization of your first
codenjoy event.

Here is the repository [https://github.com/codenjoyme/codenjoy-game](https://github.com/codenjoyme/codenjoy-game).
You have to figure out how to fork a project for yourself, how commit is done in git.

Sample game - Sample
--------------

Sample is an example of a single-board game with all the necessary artifacts. Learn how the project works.

- import the `sample` project as `maven project` into idea
- run all the tests, they should pass - you should observe the green bar
- go to [sample/src/test/java/com/codenjoy/dojo/sample/model/SampleTest.java](https://github.com/codenjoyme/codenjoy-game/blob/master/sample/src/test/java/com/codenjoy/dojo/sample/model/SampleTest.java)
and see how the tests are written for the game.
- go to [sample/src/main/java/com/codenjoy/dojo/sample](https://github.com/codenjoyme/codenjoy-game/blob/master/sample/src/main/java/com/codenjoy/dojo/sample)
and see what you need to write the minimum for the new game.
- here in the package [sample/src/main/java/com/codenjoy/dojo/sample/client](https://github.com/codenjoyme/codenjoy-game/blob/master/sample/src/main/java/com/codenjoy/dojo/sample/client)
The client code is located, part of which will be sent to the player as a template for the game.
- in the package [sample/src/main/java/com/codenjoy/dojo/sample/client/ai](https://github.com/codenjoyme/codenjoy-game/blob/master/sample/src/main/java/com/codenjoy/dojo/sample/client/ai)
Your AI algorithm is located, which will automatically connect to the player and play with him.
- everything else is a game engine.
- to implement a new game, it is worthwhile to deal with the main interfaces and classes of the framework.
All of them are located in the dependency engine. You should be interested in such:
* `src/main/java/com/codenjoy/dojo/services/Game.java`
* `src/main/java/com/codenjoy/dojo/services/Joystick.java`
* `src/main/java/com/codenjoy/dojo/services/Printer.java`
* `src/main/java/com/codenjoy/dojo/services/GameType.java`
* `src/main/java/com/codenjoy/dojo/services/Tick.java`
* `src/main/java/com/codenjoy/dojo/services/PlayerScores.java`
* `src/main/java/com/codenjoy/dojo/services/Point.java`
* `src/main/java/com/codenjoy/dojo/services/Printer.java`
* `src/main/java/com/codenjoy/dojo/services/GamePrinter.java`
* `src/main/java/com/codenjoy/dojo/services/EventListener.java`
* `src/main/java/com/codenjoy/dojo/services/Dice.java`
* `src/main/java/com/codenjoy/dojo/services/CharElements.java`
* `src/main/java/com/codenjoy/dojo/services/Direction.java`
* `src/main/java/com/codenjoy/dojo/services/Settings.java`
* `src/main/java/com/codenjoy/dojo/client/AbstractBoard.java`
* `src/main/java/com/codenjoy/dojo/client/Solver.java`
* `src/main/java/com/codenjoy/dojo/client/Direction.java`
- all of these are basic interfaces / classes, with their help the new game is being integrated into
main framework (as a cartridge in the dendy console).
- study their description in interfaces to classes and dependency engine and sample project classes

New game development
--------------

To develop your game, it is not necessary to write all classes from scratch - take the `sample` project as a basis.

- copy the contents of the `sample` folder into the` mygame` folder (any name) and rename the `Sample` classes to` MyGame`.
- your goal is good code coverage with tests that we can trust,
because the game should be developed by TDD, if you are not familiar with it -
[рекомендуем книгу Кента Бека](http://www.ozon.ru/context/detail/id/1501671/).
- source for the game for the client maven will automatically collect in zip, as it is done
[sample/src/main/webapp/resources/user/sample-servers.zip](https://github.com/codenjoyme/codenjoy-game/blob/master/sample/src/main/webapp/resources/user)
Note that the `pom.xml` file has a section `maven-antrun-plugin`,
where ant'om going to this zip. It gets `pom.xml` itself,
the `Elements` class from the model package and everything from the `client` package except for the `ai` package.
- write the manual for the game, just as we did here
[sample/src/main/webapp/resources/help/sample.html](https://github.com/codenjoyme/codenjoy-game/blob/master/sample/src/main/webapp/resources/help/sample.html)
- draw sprites - these are square pictures, on the basis of which will be
Draw a game in the browser. Usually they are freely available on the network.
Png files with sprites are contained in the [sample/src/main/webapp/resources/sprite/sample/](https://github.com/codenjoyme/codenjoy-game/blob/master/sample/src/main/webapp/resources/sprite/sample).
Important! The names of the sprites are not chosen arbitrarily, but in conjunction with the enum fields.
[sample/src/main/java/com/codenjoy/dojo/sample/model/Elements.java](https://github.com/codenjoyme/codenjoy-game/blob/master/sample/src/main/java/com/codenjoy/dojo/sample/model/Elements.java).
All names must be lover case
- then implement your bot by analogy with [sample/src/main/java/com/codenjoy/dojo/sample/client/ai/ApofigSolver.java](https://github.com/codenjoyme/codenjoy-game/blob/master/sample/src/main/java/com/codenjoy/dojo/sample/client/ai/ApofigSolver.java)
- run this code to check how your bot plays the game
```
    public static void main(String[] args) {
        LocalGameRunner.run(new GameRunner(),
                new YourSolver(new RandomDice()),
                new Board());
    }
```
- collect jar-file, for this execute the command `mvn package` in the root of the sample folder
- jar will be in `sample\target\sample-engine.jar`
- send it to us at [apofig@gmail.com](mailto:apofig@gmail.com) with the theme `New game for codenjoy`

Thank!

Other materials
--------------
More [details here](https://github.com/codenjoyme/codenjoy)

[Codenjoy team] (http://codenjoy.com/portal/?page_id=51)
===========