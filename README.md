# Mirror site

### compile

This site uses Jekyll transformation, compiled into ECMAScript6 with babel, so you must install ruby >= 2.0 and NodeJS.

### For Centos
1.install nodejs
```
yum install nodejs
```
2.install ruby 2.2.4 and rubygems

Step 1: Install Required Packages
```
yum install gcc-c++ patch readline readline-devel zlib zlib-devel
yum install libyaml-devel libffi-devel openssl-devel make
yum install bzip2 autoconf automake libtool bison iconv-devel sqlite-devel
```
Step 2: Compile ruby 2.2.4 source code
```
wget -c https://cache.ruby-lang.org/pub/ruby/2.2/ruby-2.2.4.tar.gz
```
Step 3: Install rubygems
```
wget -c https://rubygems.org/rubygems/rubygems-2.4.8.tgz
ruby setup.rb
```
3. install bundle and build
```
gem install bundle
gem install build
```
4. Fork mirrors source code

```
bundle install
jekyll build
```

For running, you need to download some dynamic data files.

```
wget https://mirrors.tuna.tsinghua.edu.cn/static/tunasync.json -O static/tunasync.json
wget https://mirrors.tuna.tsinghua.edu.cn/static/tunet.json -O static/tunet.json
mkdir -p static/status
wget https://mirrors.tuna.tsinghua.edu.cn/static/status/isoinfo.json -O static/status/isoinfo.json
```

Now you can run the "jekyll serve" command to see the effect.



### This project is the "mirror-web" project of Fork TUNA.

