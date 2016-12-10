# Robocode-maven

A framework for easy development and sharing of [Robocode](http://robocode.sourceforge.net/) robots, setup as a [Maven](https://maven.apache.org/) project and adapted to work with the containerized [Robocode-docker](https://github.com/fbcbarbosa/robocode-docker).

## Requirements

To build the project you'll require `maven` and to run [Robocode-docker](https://github.com/fbcbarbosa/robocode-docker) you'll need `docker`.

## Installation

1. Clone Robocode-maven where you want it installed. A good place to pick is `$HOME/robocode` (but you can install it somewhere else).

  ```
  $ git clone https://github.com/fbcbarbosa/robocode-maven/ ~/robocode
  ```

2. Define the environment variable `ROBO_ROOT` to point to the path where the repo is cloned and add `$ROBO_ROOT` to your $PATH for access to the pyenv command-line utility.

  ```
  $ echo 'export ROBO_ROOT="$HOME/robocode"' >> ~/.bashrc 
  $ echo 'export PATH="$ROBO_ROOT:$PATH"' >> ~/.bashrc
  ```
  
3. Restart your shell so the path changes take effect.

  ```
  $ exec $SHELL
  ```

4. Build the project one time using Maven. It will download all the required packages once, including the Robocode API, so be a little patient.

  ```
  $ cd $ROBO_ROOT && mvn clean install
  ```

5. Run 'robo' script to launch [Robocode-docker](https://github.com/fbcbarbosa/robocode-docker). The first time may take a while as it downloads the 'fbcbarbosa/robocode' image.

  ```
  $ robo
  ```

And that's it!
  
## Developing robots

Simply add the repository to your favorite IDE as a Maven Project. Now make sure that every robot is added under the `robots` package, within the `$ROBO_ROOT/src/main/java/robots` folder. Feel free to add subpackages though, e.g. `robots.myrobot` at `$ROBO_ROOT/src/main/java/robots/myrobots`.

To build your robots run Maven on the root of the installation folder:

```
$ cd $ROBO_ROOT && mvn clean install
```

They will then become instantly available on Robocode (even if it is already running) under the `robots.*` package.

> **Note:** you *can* use Robocode's functional, yet limited, IDE to develop your robots, even as it's running on a container. However it will be hard to retrieve them at the host machine later, so it's not recommended. Besides, if you're ok using Robocode's IDE, why'd you download this framework?

Don't forget to commit your robots on a public GitHub repository so that everyone can learn from them :)
