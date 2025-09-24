> [!cite]- **Hello and welcome back.**  
> 안녕하세요, 다시 만나서 반갑습니다.

> [!cite]- **In this lecture I want to explore the concept of build contexts.**  
> 이번 강의에서는 **빌드 컨텍스트(Build Context)** 개념을 탐구해보려고 합니다.

> [!cite]- **We have been building Docker images based on Docker files for a while now, so it does make sense that we spend some time to understand what a build context is and how this relates to the Docker daemon, and to the Docker files that we write for us.**  
> 우리는 지금까지 **Dockerfile**을 기반으로 **Docker 이미지**를 빌드해왔는데요,  
> 빌드 컨텍스트가 무엇인지, 그리고 이것이 **Docker Daemon** 및 우리가 작성하는 **Dockerfile**과 어떤 관계가 있는지 이해하는 것이 중요합니다.

> [!cite]- **To better visualize this, let's first of all just create a very simple index.js file.**  
> 이를 좀 더 시각적으로 이해하기 위해, 먼저 아주 간단한 `index.js` 파일을 생성해 보겠습니다.

> [!cite]- **All this file will do is just console, log a message, a hello from node, and we're going to write a docker file for us to actually execute this index.js.**  
> 이 파일에서는 단순히 콘솔에 **"Hello from Node"** 메시지를 출력하는 기능을 구현할 것입니다.  
> 그리고 이 `index.js` 파일을 실행할 수 있도록 **Dockerfile**을 작성해 보겠습니다.

> [!cite]- **Let's just create a new docker file here.**  
> 새로운 **Dockerfile**을 하나 만들겠습니다.

> [!cite]- **And this Docker file will start with a from node colon 22.**  
> 그리고 이 **Dockerfile**은 `FROM node:22`로 시작할 것입니다.

> [!cite]- **And for the sake of doing things a little bit different, let's just use the alpine version of node 22.**  
> 이번에는 기존과 조금 다르게 해보기 위해 **Node.js 22 Alpine 버전**을 사용해 보겠습니다.

> [!cite]- **Since we have a completely clean JavaScript project here without any dependencies, we do not need to have a package.json or a package-lock.json.**  
> 현재 프로젝트는 **완전히 깨끗한 JavaScript 프로젝트**이며,  
> 추가적인 **의존성(dependencies)** 없이 단순한 실행 파일만 필요합니다.  
> 따라서 `package.json`이나 `package-lock.json` 파일이 없어도 괜찮습니다.

> [!cite]- **We can just directly copy all the files from our directory into our container.**  
> 우리는 프로젝트 디렉토리의 모든 파일을 컨테이너 내부로 직접 복사할 수 있습니다.

> [!cite]- **Let's change the Workdir here to forward slash app beforehand.**  
> 작업 디렉토리를 먼저 **`/app`**으로 변경하겠습니다.

> [!cite]- **Let's copy all the files and then let's just have a command here which will be node colon index.js.**  
> 모든 파일을 복사한 후, 실행 명령을 `node index.js`로 설정하겠습니다.

> [!cite]- **Once we save this we can now come back to the terminal.**  
> 파일을 저장한 후, 터미널로 돌아갈 수 있습니다.

> [!cite]- **And let's check that we have all the files here in the directory.**  
> 현재 디렉토리에 모든 파일이 있는지 확인해보겠습니다.

> [!cite]- **Perfect.**  
> 완벽합니다.

> [!cite]- **So now we can run Docker build.**  
> 이제 **Docker 빌드** 명령어를 실행할 수 있습니다.

> [!cite]- **Let's tag this here from hello from node.**  
> 태그를 `hello-from-node`로 지정하겠습니다.

> [!cite]- **And when we pass a dot I have already mentioned this, but I didn't really spend too much time explaining what it means.**  
> 마지막에 **`.`(점)**을 사용하는 이유에 대해서는 간단히 언급한 적이 있지만, 이번 강의에서 더 깊이 설명할 것입니다.

> [!cite]- **And this dot here is the context.**  
> 여기서 사용하는 **`.`(점)**이 바로 **컨텍스트(Context)**입니다.

> [!cite]- **Now what does a context?**  
> 그렇다면 **컨텍스트**란 무엇일까요?

> [!cite]- **A build context means basically a build context refers to all the files and subdirectories and all the content that is required by our Docker file in order to build the image.**  
> **빌드 컨텍스트(Build Context)**란 기본적으로 **Dockerfile**이 이미지를 빌드하는 데 필요한 모든 파일과 하위 디렉터리 및 내용을 의미합니다.

> [!cite]- **This context here will be uploaded to the Docker host to the docker daemon, because the build process is not run in the docker CLI.**  
> 이 **컨텍스트**는 **Docker 호스트(Docker Host)**와 **Docker 데몬(Docker Daemon)**으로 업로드됩니다.  
> 왜냐하면 **빌드 과정(Build Process)**은 **Docker CLI**에서 실행되는 것이 아니기 때문입니다.

> [!cite]- **We are just triggering the build process.**  
> 우리는 단순히 **빌드 과정**을 **트리거(Trigger)**할 뿐입니다.

> [!cite]- **But the build is executed once again by the docker daemon by the Docker server in our machines.**  
> 그러나 **실제 빌드 과정**은 다시 한 번 **Docker 데몬** 및 **Docker 서버**에 의해 실행됩니다.

> [!cite]- **If you are using Docker locally here, it just happens that the Docker CLI and the Docker server, they are both running at the same machine.**  
> 만약 로컬 환경에서 **Docker**를 사용하고 있다면,  
> **Docker CLI**와 **Docker 서버**가 **같은 머신에서 실행**되는 상황일 것입니다.

> [!cite]- **But this might also be the case that the docker cli is running in your machine, for example, but it is connected to a remote host.**  
> 하지만 **Docker CLI**가 **사용자의 머신에서 실행**되고 있을지라도,  
> 이를 **원격 호스트(Remote Host)**에 연결하는 경우도 있습니다.

> [!cite]- **So this context here will be uploaded to the Docker host, which is then responsible for building the image.**  
> 따라서 이 **컨텍스트**는 **Docker 호스트**에 업로드되며,  
> 이 호스트가 **이미지 빌드(Building the Image)**를 담당하게 됩니다.

> [!cite]- **And since the Docker host might be separated from the machine which is issuing the build command, then the Docker host doesn't really necessarily has the same set of files.**  
> 그리고 **Docker 호스트**는 **빌드 명령을 실행하는 머신과 분리될 수 있기 때문에**,  
> 항상 **같은 파일 세트(File Set)**를 가지고 있지는 않을 수도 있습니다.

> [!cite]- **So what this will do is it will upload all the informed context here to the Docker host.**  
> 그렇기 때문에, **Docker 호스트**로 **모든 지정된 컨텍스트를 업로드**하는 과정이 필요합니다.

> [!cite]- **Great.**  
> 좋습니다.

> [!cite]- **Let's run this command here and see what's going to happen.**  
> 이제 명령어를 실행하고 **무슨 일이 일어나는지** 살펴보겠습니다.

> [!cite]- **You will see here if we inspect the first few lines you can see that there is a transferring context here.**  
> 첫 번째 몇 줄을 확인하면, **컨텍스트가 전송(Transferring Context)**되고 있는 것을 볼 수 있습니다.

> [!cite]- **There is also a loading a docker ignore file as well as some metadata.**  
> 또한 **`.dockerignore` 파일 로딩**과 **메타데이터(Metadata)**가 포함되어 있습니다.

> [!cite]- **But for us, these two lines here are interesting.**  
> 그러나 우리가 주목할 부분은 바로 **이 두 줄**입니다.

> [!cite]- **So we are loading something called a docker. Ignore that we did not explore yet and then we are transferring the context.**  
> 우리는 아직 살펴보지 않은 **`.dockerignore` 파일**을 로드한 뒤,  
> 이제 **컨텍스트를 전송**하고 있습니다.

> [!cite]- **This context here is very small because we have just an index.js file.**  
> 이 컨텍스트는 매우 작습니다, 왜냐하면 `index.js` 파일 하나만 있기 때문입니다.

> [!cite]- **If we scroll down here a little bit and we just run the Docker images, then we will see that we have our hello from node.**  
> 조금 아래로 스크롤해서 `docker images` 명령어를 실행하면,  
> `hello-from-node` 이미지가 생성된 것을 확인할 수 있습니다.

> [!cite]- **And if we were to compare this here with our previous express image, you can see that this is almost ten times smaller.**  
> 이 이미지를 이전 **Express** 기반 이미지와 비교해 보면,  
> 크기가 **거의 10배 더 작다는 것**을 알 수 있습니다.

> [!cite]- **And we have just changed the base image.**  
> 우리는 단순히 **베이스 이미지(Base Image)**만 변경했을 뿐입니다.

> [!cite]- **If we were to just out of curiosity here Docker history.**  
> 호기심 삼아 `docker history` 명령어를 실행해 보면,

> [!cite]- **Hello from node we will see.**  
> `hello-from-node` 이미지의 기록을 확인할 수 있습니다.

> [!cite]- **Let's once again reduce the size a little bit.**  
> 이미지 크기를 한 번 더 줄여보겠습니다.

> [!cite]- **Here you will see that it has considerably fewer layers.**  
> 여기에서 **훨씬 더 적은 수의 레이어(Layers)**가 있는 것을 확인할 수 있습니다.

> [!cite]- **So let's just now run here Docker History Express Dash app once again without clearing the console.**  
> 콘솔을 초기화하지 않고 **`docker history express-app`** 명령어를 실행해 보겠습니다.

> [!cite]- **And then here you can see the big difference.**  
> 그러면 **큰 차이(Big Difference)**가 나타납니다.

> [!cite]- **This one once again has those big big layers.**  
> 이전 이미지에는 **매우 큰 레이어들**이 포함되어 있습니다.

> [!cite]- **While this image here the alpine image has considerably less.**  
> 반면에 **Alpine 기반의 이미지**는 **훨씬 적은 레이어를 포함**하고 있습니다.

> [!cite]- **Anyways, I'm diverging from the content here.**  
> 아무튼, 지금 원래 내용에서 조금 벗어났네요.

> [!cite]- **Let's go back to our current Docker images here.**  
> 다시 현재 **Docker 이미지 목록**으로 돌아가겠습니다.

> [!cite]- **To inspect that, we now have our hello from node.**  
> 이를 확인하기 위해, 현재 `hello-from-node` 이미지가 존재하는 것을 볼 수 있습니다.

> [!cite]- **Let me just quickly adjust here the zoom and that this image here was also built based on this Docker file.**  
> 줌을 빠르게 조정하여 확인하면,  
> 이 이미지 또한 **해당 Dockerfile을 기반으로 생성되었음**을 알 수 있습니다.

> [!cite]- **Now this process was fairly quick because our directory once again it has very light files.**  
> 이번 **빌드 과정(Build Process)**은 비교적 빠르게 진행되었는데,  
> 그 이유는 현재 디렉토리가 **매우 가벼운 파일들**로 구성되어 있기 때문입니다.

> [!cite]- **Right.**  
> 맞습니다.

> [!cite]- **So this directory here has very small files.**  
> 이 디렉토리는 **매우 작은 파일들**을 포함하고 있습니다.

> [!cite]- **There is nothing heavy to be uploaded.**  
> 업로드할 **무거운 파일(Heavy Files)**이 없습니다.

> [!cite]- **However whenever we are running a docker build command and we are passing the whole context here, it just so happens that if we have some heavy directories, maybe some dependencies like node modules, directory with several dependencies or some other, maybe a Python virtual environment or something, this can have several hundred megabytes.**  
> 그러나 우리가 **Docker 빌드 명령어**를 실행하고 전체 **컨텍스트(Context)**를 전달할 때,  
> 만약 **무거운 디렉토리(Heavy Directories)**가 포함되어 있다면,  
> 예를 들어 **`node_modules`** 같은 의존성 파일들이 많거나,  
> **Python 가상 환경(Virtual Environment)**이 포함되어 있는 경우,  
> 파일 크기가 **수백 메가바이트(MB)**에 이를 수도 있습니다.

> [!cite]- **And if we just pass the context like so, then this will all be uploaded to the Docker host.**  
> 이렇게 컨텍스트를 전달하면, 모든 데이터가 **Docker 호스트**로 업로드됩니다.

> [!cite]- **So we can simulate this by creating some fake file in Mac.**  
> 이를 **Mac 환경에서 가상의 파일을 생성하는 방식**으로 **시뮬레이션**할 수 있습니다.

> [!cite]- **This is the MK makefile command here.**  
> 여기서는 **MK makefile** 명령어를 사용할 것입니다.

> [!cite]- **So I'm just going to say makefile dash n.**  
> 따라서 `makefile -n` 명령어를 입력할 것입니다.

> [!cite]- **And then we can create something with I don't know ten gigabytes.**  
> 그리고 **10GB 크기의 파일을 생성**할 수도 있습니다.

> [!cite]- **Or if you have just 1GB or 5GB.**  
> 혹은 **1GB 또는 5GB**로 설정할 수도 있습니다.

> [!cite]- **Let's go with five gigabytes.**  
> 여기서는 **5GB**를 선택하겠습니다.

> [!cite]- **And we're just going to say here some dash large dash file.**  
> `some-large-file`이라는 이름으로 파일을 생성하겠습니다.

> [!cite]- **Once we create that it will take a little bit of time to create one file with five gigabytes.**  
> 이 파일을 생성하는 데는 **약간의 시간이 소요**될 것입니다.

> [!cite]- **But once that is done, let's have a look here.**  
> 하지만 생성이 완료되면 **확인해보겠습니다**.

> [!cite]- **Once again we have our very large file.**  
> 다시 한 번 **매우 큰 파일**이 생성된 것을 확인할 수 있습니다.

> [!cite]- **Right.**  
> 그렇습니다.

> [!cite]- **So this is some large file here.**  
> 이 파일은 **매우 큰 파일**입니다.

> [!cite]- **And now let's clear the console.**  
> 이제 **콘솔을 정리(Clear Console)**하겠습니다.

> [!cite]- **And now the moment we run.**  
> 이제 **명령어를 실행할 순간**입니다.

> [!cite]- **And this is a fairly heavy command because once again let's inspect our Docker file.**  
> 이 명령어는 **상당히 무거운 작업(Heavy Command)**입니다.  
> 한 번 더 **Dockerfile을 확인**해보겠습니다.

> [!cite]- **We are copying all the files into our container so that five gigabytes file will actually be copied into the container.**  
> 우리는 **모든 파일을 컨테이너 내부로 복사**하고 있습니다.  
> 따라서 **5GB 크기의 파일**도 **컨테이너 내부로 복사**될 것입니다.

> [!cite]- **So for us here we will simply say docker build hello from node.**  
> 여기서 우리는 간단히 `docker build hello-from-node` 명령어를 실행할 것입니다.

> [!cite]- **Let's clear the console, run this and let's wait.**  
> 콘솔을 정리하고 명령어를 실행한 후 **잠시 기다리겠습니다**.

> [!cite]- **Now you can see that we are transferring the context.**  
> 이제 **컨텍스트를 전송(Transferring Context)**하고 있는 것을 확인할 수 있습니다.

> [!cite]- **And the context is very large.**  
> 그리고 **컨텍스트의 크기가 매우 큽니다**.

> [!cite]- **It is five gigabytes.**  
> **컨텍스트 크기는 5GB**입니다.

> [!cite]- **So it is taking a lot of time for the docker build command to actually upload the file from our local machine from the local directory to the docker host.**  
> 따라서 **Docker 빌드 명령어**가 **로컬 머신(Local Machine)에서 Docker 호스트로 파일을 업로드하는 데 시간이 오래 걸리는 것**을 확인할 수 있습니다.

> [!cite]- **Once again, we are running this locally, right?**  
> 다시 말해, 우리는 이 작업을 **로컬 환경에서 실행**하고 있습니다.

> [!cite]- **You can see here that the copy command also takes five seconds.**  
> 여기에서 **파일 복사(Copy Command)**에도 **5초가 소요**되는 것을 볼 수 있습니다.

> [!cite]- **The exporting layers is also taking a lot of time.**  
> 레이어를 **내보내는(Exporting Layers)** 과정도 많은 시간이 걸립니다.

> [!cite]- **And if we were to actually run and visualize our images here, you will see that our image has five gigabytes.**  
> 그리고 우리가 **이미지를 실행하고 확인(Visualize Images)**하면,  
> 해당 이미지의 크기가 **5GB**임을 알 수 있습니다.

> [!cite]- **Hopefully this gives a little bit of clarity around what the context is.**  
> 이 과정이 **컨텍스트(Context)**에 대한 이해를 돕기를 바랍니다.

> [!cite]- **It's basically all the files in the current directory that are then used in our image during the build command and considering our Docker file, let's quickly edit our Docker file.**  
> **컨텍스트**란 기본적으로 **현재 디렉토리에 있는 모든 파일을 포함**하며,  
> 이를 **이미지 빌드 과정(Build Command)**에서 사용하는 것입니다.  
> 그렇다면 **Dockerfile을 빠르게 수정**해보겠습니다.

> [!cite]- **We can either use vim or we can come to the IDE and instead of copying all the files, let's change this.**  
> 우리는 `vim`을 사용하거나 **IDE에서 수정**할 수 있습니다.  
> 그리고 **모든 파일을 복사하는 대신** 이 부분을 변경하겠습니다.

> [!cite]- **And let's simply copy the index dot js into index dot js like so.**  
> 그리고 `index.js` 파일만 단순히 복사하도록 변경하겠습니다.

> [!cite]- **So we're just copying a single file here.**  
> 즉, **하나의 파일**만 복사하는 방식으로 수정하는 것입니다.

> [!cite]- **Let's save this and come back to the terminal to build our image again.**  
> 이제 파일을 저장하고 **터미널로 돌아가서 다시 빌드(Build Image)**하겠습니다.

> [!cite]- **Once we come back to the terminal and we run docker build with the same tag and the same context here.**  
> 터미널에서 동일한 태그(Tag)와 동일한 **컨텍스트(Context)**로 **`docker build` 명령어를 실행**하겠습니다.

> [!cite]- **Let's run this.**  
> 이제 실행하겠습니다.

> [!cite]- **And now as you can see, Docker is smart enough to identify.**  
> 이제 확인하면,  
> **Docker는 매우 똑똑하게 파일을 인식(Identify)**하고 있습니다.

> [!cite]- **Here you can see this transferring context to bytes here.**  
> 여기에서 **컨텍스트를 바이트 단위로 전송(Transferring Context to Bytes)**하는 것을 볼 수 있습니다.

> [!cite]- **Docker is smart enough to identify that that large file is not necessary in the Docker file.**  
> **Docker는 이 대용량 파일(Large File)이 Dockerfile에 필요하지 않다는 것을 인식**합니다.

> [!cite]- **It's not needed and it's not going to transfer it to the Docker host.**  
> 필요하지 않은 파일이므로 **Docker 호스트로 전송되지 않습니다**.

> [!cite]- **If it were to then also have a look at Docker images.**  
> 그렇다면 `docker images` 명령어를 실행해 보겠습니다.

> [!cite]- **We will see that the new image is actually very small, and even though the large file is still in our directory here, it was not uploaded to the docker host.**  
> 새롭게 생성된 이미지의 크기가 **매우 작다는 것**을 확인할 수 있으며,  
> 비록 대용량 파일이 **우리의 디렉토리에 남아 있지만**,  
> 이 파일은 **Docker 호스트로 업로드되지 않았습니다**.

> [!cite]- **There is still another topic I would like to discuss with you, which is the concept of a docker ignore file.**  
> 이제 **또 다른 중요한 개념**을 소개하겠습니다.  
> 바로 **`.dockerignore` 파일(Docker Ignore File)**입니다.

> [!cite]- **Since we will also work with this large file, I'm not going to delete this for now, I'm just going to leave it in my machine.**  
> 우리는 이 대용량 파일을 사용해야 하므로,  
> 지금 당장은 **삭제하지 않고 머신에 그대로 두겠습니다**.

> [!cite]- **I will also leave the images here, but if you wish to go ahead and do some cleanup because of space concerns, then by all means just go ahead and delete these files here.**  
> 이미지 역시 그대로 둘 것입니다.  
> 하지만 **공간 문제(Space Concern)**로 인해 **정리하고 싶다면**,  
> 자유롭게 **파일을 삭제(Delete Files)**하시면 됩니다.

> [!cite]- **Otherwise you can leave them.**  
> 그렇지 않다면, 그냥 **파일을 그대로 유지**해도 됩니다.

> [!cite]- **Let's take a short break and come back in the next lecture.**  
> 이제 **잠시 휴식**을 취하고, **다음 강의에서 다시 돌아오겠습니다**.
