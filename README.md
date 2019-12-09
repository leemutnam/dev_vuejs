# Front
> vue.js + webpack

> version: node.js 12.0, npm 6.0, vue.js 2.6, vue/cli 4.0, webpack 3.0, 

> init setup: vue init webpack

> editor / debug tool: pycharm

> pycharm plugin: Nodejs, Remote Interpreter, Vue.js
## Set-Up
1. config 추가
```
$ touch _provisioning/configuration/root/etc/config.json
```
2. id_rsa 추가
```
$ cp ~/.ssh/id_rsa _provisioning/configuration/root/.ssh/
```
3. 프로젝트 이름 및 경로 수정
```
config.json -> vagrant.name = {project name}
config.json -> git.repo = {remote repository}
common.yml -> project_path = opt/{project name}
```
4. 가상환경 생성
```
cd _provisioning
vagrant up
```
5. pycharm SFTP 연동
```
Tools - deployment - configuration - connection/mapping
Tools - deployment - check Automatic Upload
```
6. 개발환경 시작
```
vagrant ssh
cd /opt/{project name}
npm run start
```
## Build Setup

```
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run all tests
npm test
```

## 이슈
```
linux에서 npm 으로 phantomjs 를 설치할 경우 에러가 발생함.
npm 으로 phantomjs-prebuilt 패키지를 설치하면 
phantomjs에 대한 링크를 만들고 (sudo 권한 필요) phantomjs 에 의존성을 지닌 패키지 설치시 에러가 발생하지 않는다 
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
