# tracker

This main module is to use chihaya to run a tracker. You should clone [this repository](https://github.com/whr819987540/tracker) and [chihaya](https://github.com/chihaya/chihaya) under the same directory.

```bash
git clone https://github.com/whr819987540/tracker.git
git clone https://github.com/chihaya/chihaya.git
```

The directory tree should look like this:

```bash
├── chihaya
└── tracker
```

Then you build the tracker from source code with the commands below.

```bash
cd tracker
source build.sh
```

As for running the tracker, modify the tracker/config.yaml first. 
If you would like to use redis to store peer info, run below.

```bash
docker pull redis:alpine3.18
docker run -d -p 6379:6379 --name redis redis:alpine3.18
docker exec -it redis redis-cli
```

After the configuration, run the tracker。

```bash
# debug
./tracker --config ./config.yaml --debug
# OR
nohup ./tracker --config ./config.yaml >> tracker.log --debug 2>&1 &
# no debug
./tracker --config ./config.yaml
# OR
nohup ./tracker --config ./config.yaml >> tracker.log 2>&1 &
```

