# Example: Debian Buster build environment with Cpp

## Prepare

Download and install [Docker](https://www.docker.com/) for your host machine.

## Project tree

```plaintext
.
├─ createvenv
│  └─ DockerBuildEnvScript
├─ src
│  └─ main.cpp
├─ .gitignore
├─ CMakeLists.txt
└─ readme.md
```

## Step by step building

On host terminal:
- Get git: `curl https://github.com/Vadivank/cppvenv.git`
- Go to project dir: `cd cppvenv`
- Pull Debian image for building: `docker image pull debian:10.13`
- Build cppvenv: `docker build -t busterenv/busterenv_build:0.1 -f createvenv/DockerBuildEnvBuster .`
- Run cppvenv image: `docker run -it --rm -v %CD%:/src busterenv/busterenv_build:0.1 bash`

On venv terminal:

- Copy public headers for Boost: `cp -r /root/boost_1_77_0/boost /src/boost`
- Go to project dir: `cd ~`
- Build project: 
  - `cmake . -Bbuild`
  - `cmake --build build`
- Run app: `build/a.out`
