# Doecker
just Down docker
[link](https://docs.docker.com/engine/install/)

- Pull docker image (at ngc catalog / [link](https://catalog.ngc.nvidia.com/containers))
``` shell
$docker pull @contianer name
```

- check image
```
$docker images
> REPOSITORY               TAG         IMAGE ID       CREATED       SIZE
> nvcr.io/nvidia/pytorch   24.01-py3   06ffccc5de6e   10 days ago   19.4GB
```
- image remove
```
$docker rmi [imageid]
```
 - docker create 
	 - make container 

 - docker start 
	 - start container

- check container 
```
$ docker ps
```

- container delete
```
$ docker rm [container id],[container id]
```

 - run docker (= create+start)
```
$docker run <option> <image> <command> <argument>
```

- run option
	```bash
		$ docker run -it ubuntu:20.04
		root@ad9785df1f26:/
	```
	- -i : 컨테이너에 attach(접속)하지 않은 상태여도 표준입력(stdin)을 활성화하고 유지한다
	- -t : TTY 모드(pseudo-TTY)를 사용하는 것으로, 쉘에 명령어를 작성할 수 있다.
	- -it :  두 옵션을 모두 적용하여 docker는 pseudo-TTY를 할당하고, container의 stdin에 연결한다. 
	```bash
		$ docker run -d ubuntu:20.04 echo "test"
		dbb2e4d820def34b8970dcfd4e66ef27cb4b9bd13431568370d5f58c749f7a69
	```
	- -d : 이 옵션은 컨테이너를 백그라운드에서 실행하도록 하는 옵션이다. 실행한 container id를 출력한다.
	```bash
		$ docker run -e APP_ENV=production -e APP2_ENV=dev ubuntu:20.04 env
		PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
		HOSTNAME=6049820fc843
		APP_ENV=production
		APP2_ENV=dev
		HOME=/roo
	```
	- -e : 이 옵션은 컨테이너에 환경 변수를 추가하는 옵션이다. 환경 변수 여러개를 추가하고 싶다면 위 예제처럼 `-e`를 여러번 사용해야 한다.
	```bash
		$ docker run -p 127.0.0.1:80:8080 ubuntu:20.04 bash
	```
	- -p : 이 옵션은 호스트에 연결된 컨테이너의 특정 포트를 외부에 노출하기 위해 사용한다. 보통 웹서버의 포트를 외부로 노출하기 위해 사용한다. 위 예제는 컨테이너의 `8080` 포트를 호스트의 `127.0.0.1` ip의 `80` 포트에 binding 한 것이다.
	```bash
		$ docker run -w /path/to/dir/ ubuntu:20.04 pwd
		/path/to/dir/
	```
	- -w : 컨테이너의 working directory를 변경하는 옵션이다.
	```bash
		$ echo arrow==1.0.3 > requirements.txt
		$ docker run --rm -v `pwd`:/opt ubuntu:20.04 cat /opt/requirements.txt
		arrow==1.0.3
	```
	- -v : 이 옵션은 현재 working directory를 컨테이너에 마운트 하는 옵션이다. `-v <호스트 디렉터리>:<컨테이너 디렉터리>` 와 같이 사용한다.
	```bash
		$ docker run -u minseop ubuntu:20.04 bash
	```
	- -u : 이 옵션은 특정 user 또는 uid로 컨테이너에 접속하기 위해 사용하는 옵션이다. `RUN useradd minseop` 와 같이 docker image 빌드시 계정을 추가해줘야 한다.
	```bash
		$ docker run -it -h="minseop-mac" ubuntu:20.04
		root@minseop-mac:/#
	```
	- -h : 이 옵션은 컨테이너의 호스트 네임을 설정하는 옵션이다.
	```bash
		$ docker run --name ubuntu-test-container ubuntu:20.04 bash
		$ docker ps -a 
		CONTAINER ID   IMAGE          COMMAND   CREATED         STATUS                     PORTS     NAMES
		7fe4d35c8e23   ubuntu:20.04   "bash"    5 seconds ago   Exited (0) 4 seconds ago             ubuntu-test-container
	```
	- --name : 이 옵션은 컨테이너의 이름을 설정할 때 사용하는 옵션이다.
	```bash
		$ docker run --rm ubuntu:20.04 echo "run command, then container deleted" 
	```
	- 이 옵션은 명령어 수행 후 container가 삭제 되도록 하는 옵션이다. 컨테이너를 일회성으로 사용할 때 주로 사용한다.

- docker commit (save now container)
	```
		$docker commit (id || imagename) (save imagename)
	```


도커 설치 -> 도커 pull 을 이용해 hub 또는 ngc catalog 에서 이미지 다운 -> 다운받은 이미지를 run 을 사용해 실행 -> 세팅 -> commit 을 이용해 저장 

#docker #image #ngc-catalog #VM #Virtual_Machine #container
