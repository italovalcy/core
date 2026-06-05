# Building Debian packages

Here are the step-by-step to build the debian packages:

```
docker run -d --name debian13 debian:trixie sleep infinity
docker exec -it debian13 bash
git clone --branch build/package_debian_13 https://github.com/italovalcy/core.git
cd core/
apt update
apt install -y sudo ruby ruby-dev build-essential rubygems
gem install fpm
./setup.sh
source ~/.bashrc
inv build -i debian
```

After running the steps above, you sould have a file at `/core/core_9.2.1_amd64.deb`, which you can copy and install on the target system.
