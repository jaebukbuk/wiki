1. node js stand alone zip file install  
2. cmd, gitbash, powershell 등을 이용하여 설정 확인  
3. npmrc  
  
  
```bash  
$ npm -v  
8.19.3  
  
$ ./npm -v  
11.6.2  
  
$ npm config get userconfig  
C:\Users\Hhome\.npmrc  
  
$ ./npm config get userconfig  
C:\Users\Hhome\.npmrc  
  
$ ./npm config set userconfig ./.npmrc  
  
$ ./npm config get userconfig  
C:\dev\tools\node-v24.11.1-win-x64\.npmrc  
  
```  
  
  
```bash  
  
$ npm config get prefix  
C:\Users\Hhome\AppData\Roaming\npm  
  
$ ./npm config get prefix  
C:\dev\tools\node-v24.11.1-win-x64  
  
$ ./npm install -g @openai/codex --registry=https://registry.npmjs.org/  
added 1 package in 18s  
  
$ ./npm uninstall -g @openai/codex  
  
# 글로벌 설치 디렉터리 경로 확인  
PS npm root -g  
C:\****\AppData\Roaming\npm\node_modules  
  
```  
  
