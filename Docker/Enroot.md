# [enroot](https://github.com/NVIDIA/enroot)
enroot : 루트 권한 필요없이 userspace에서 동작하는, NVIDIA에서 만든 컨테이너 런타임**이다. 
 - import 
	 - 컨테이너 이미지를 enroot 에 맞게 변환해주는 작업 
	 - @.sqsh 파일 시스템으로 저장된다.
	 - import (argument)
		  docker://[USER@][REGISTRY#]IMAGE[:TAG]  Import a Docker image from a registry
		  dockerd://IMAGE[:TAG]    lImport a Docker image from the Docker daemon
		  podman://IMAGE[:TAG]    Import a Docker image from a local Podman repository
	```
		$enroot import dockerd://(docker_images)
	```

- create 
	- .sqsh 파일을 기반의 image를 list 에 등록한다.
	```
		$enroot create --name (name) (image.sqsh)
	```

- list
	- enroot 에서 create한 이미지들을 확인 할 수 있다. 
	- option (-f) 더 자세히 볼수 있다.
	```
		$enroot list -f
	```

- start
	- list에 등록되어 있는 이미지를 컨테이너에 올려서 VM을 활성화 한다.


Docker에서 이미지 다운로드 -> import 를 통해 enroot로 변환 (.sqsh 파일로 저장됨) -> create를 통해서 enroot의 이미지 리스트에 등록(저장) -> 등록된 이미지를 start 를 통해 컨테이너에 올려 작동 

#enroot #docker #UBAI #Slurm #VM #Virtual_Machine #container