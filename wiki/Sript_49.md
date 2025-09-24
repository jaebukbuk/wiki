

> [!cite]- **Hello and welcome back.**  
> 안녕하세요, 다시 만나서 반갑습니다.

> [!cite]- **We have mentioned in several lectures that Docker has what's called a layered architecture.**  
> 여러 강의에서 Docker가 계층화된 아키텍처를 가지고 있다고 언급한 적이 있습니다.

> [!cite]- **Since we have a Docker file that now has a couple of commands here.**  
> 이제 Docker 파일에 몇 가지 명령어가 포함되어 있습니다.

> [!cite]- **So let's just get the Docker file from our containerized express app project.**  
> 그래서 컨테이너화된 Express 앱 프로젝트에서 Docker 파일을 가져옵시다.

> [!cite]- **We have a couple of commands here.**  
> 여기 몇 가지 명령어가 있습니다.

> [!cite]- **We now have the chance to explore in the CLI in the terminal here how this relates to Docker's layered architecture.**  
> 이제 CLI(명령줄 인터페이스) 터미널에서 이것이 Docker의 계층화된 아키텍처와 어떻게 관련되는지 탐색할 기회가 생겼습니다.

> [!cite]- **If you have opted to skip the project, you can download all the files.**  
> 프로젝트를 건너뛰기로 했다면, 모든 파일을 다운로드할 수 있습니다.

> [!cite]- **You can download the zip folder from the resources of this lecture.**  
> 강의 자료에서 ZIP 폴더를 다운로드할 수 있습니다.

> [!cite]- **Basically just extract the folder here and then you should get this list of files here.**  
> 기본적으로 폴더를 추출하면 다음과 같은 파일 목록이 나와야 합니다.

> [!cite]- **If you do not have the node modules here, no worries.**  
> node_modules 폴더가 없어도 걱정하지 마세요.

> [!cite]- **This is not necessary for this demo.**  
> 이 데모에서는 필요하지 않습니다.

> [!cite]- **But if you still wish to install the dependencies, you can run just npm ci from within the folder where you have extracted the files.**  
> 하지만 여전히 종속성을 설치하고 싶다면, 파일을 추출한 폴더 내에서 `npm ci`를 실행하면 됩니다.

> [!cite]- **Good.**  
> 좋습니다.

> [!cite]- **Coming back now to the Docker file, in our Docker file we have several instructions, one after the other.**  
> 이제 Docker 파일로 돌아가 봅시다. Docker 파일에는 여러 명령어가 순서대로 포함되어 있습니다.

> [!cite]- **In Docker's layered architecture, each instruction will basically lead or it will create another layer in our final image.**  
> Docker의 계층화된 아키텍처에서는 각 명령어가 기본적으로 새로운 레이어를 생성하게 됩니다.

> [!cite]- **Let's visualize this by running a Docker build command.**  
> Docker 빌드 명령을 실행하여 이를 시각화해 봅시다.

> [!cite]- **We're going to tag this as just express app.**  
> 이를 `express-app`이라는 태그를 붙여 빌드할 것입니다.

> [!cite]- **Nothing fancy here, and the context will be the folder that contains all our files, including our Docker file.**  
> 특별한 설정 없이, 컨텍스트는 Docker 파일을 포함한 모든 파일이 있는 폴더가 됩니다.

> [!cite]- **The moment we do that, if you do not have the node 22 image locally, then Docker will download it.**  
> 이 작업을 실행하면, 로컬에 Node 22 이미지가 없을 경우 Docker가 이를 다운로드할 것입니다.

> [!cite]- **It will take a few seconds to download the image and then it will finish the build.**  
> 이미지를 다운로드하는 데 몇 초가 걸리며, 이후 빌드가 완료됩니다.

> [!cite]- **We can then have a look at our Docker images.**  
> 우리는 이제 Docker 이미지들을 살펴볼 수 있습니다.

> [!cite]- **Here we will see that we have the express app image and that it has a size of 1.11GB.**  
> 여기에서 express 앱 이미지가 있으며, 크기가 1.11GB임을 확인할 수 있습니다.

> [!cite]- **We are now interested in understanding the different layers of this image.**  
> 이제 우리는 이 이미지의 다양한 레이어를 이해하는 데 관심이 있습니다.

> [!cite]- **The command for us to do that is called Docker history.**  
> 이를 수행하기 위한 명령어는 `Docker history`입니다.

> [!cite]- **And then we're going to pass the image tag.**  
> 그리고 우리는 이미지 태그를 전달할 것입니다.

> [!cite]- **We can pass the tag, or we can also pass the ID here if you wish to do so.**  
> 우리는 태그를 전달할 수도 있고, 원한다면 ID를 전달할 수도 있습니다.

> [!cite]- **I'm going to say Docker History Express Dash app, and the moment we do that, let me zoom out a little bit here so that we see everything in one line.**  
> `Docker History Express Dash app`을 입력할 것이며, 이 작업을 수행하는 순간 화면을 조금 축소하여 모든 내용을 한 줄에서 볼 수 있도록 하겠습니다.

> [!cite]- **Apologies for the slightly smaller font.**  
> 글자가 조금 작아진 것에 대해 죄송합니다.

> [!cite]- **I hope that's still readable.**  
> 그래도 읽을 수 있기를 바랍니다.

> [!cite]- **And as you can see here, what we get is actually a bunch of lines, each line potentially corresponding to an individual image.**  
> 여기에서 볼 수 있듯이, 출력 결과에는 여러 줄이 있으며 각 줄은 개별 이미지에 해당할 가능성이 있습니다.

> [!cite]- **You will also see that each line here.**  
> 또한 각 줄을 확인할 수 있습니다.

> [!cite]- **Let's have a look from bottom to top, which you can see that each line here, particularly starting at this line, this actually corresponds to the individual instructions that we have added to our Docker file.**  
> 아래에서 위로 살펴보면, 특정 줄부터 시작하여 각 줄이 우리가 Docker 파일에 추가한 개별 명령어에 해당함을 확인할 수 있습니다.

> [!cite]- **So each of these instructions is actually generating here a new image.**  
> 따라서 각 명령어가 실제로 새로운 이미지를 생성하고 있습니다.

> [!cite]- **And these images are missing because Docker is removing these images since they are not needed after the build process completes.**  
> 그리고 이러한 이미지들은 누락되었는데, 이는 빌드 프로세스가 완료된 후 필요하지 않기 때문에 Docker가 이를 삭제하기 때문입니다.

> [!cite]- **You might also be wondering where are all these images or these commands coming from?**  
> 이 모든 이미지 또는 명령어가 어디서 오는지 궁금하실 수도 있습니다.

> [!cite]- **And these commands are nothing more than the commands of our base image.**  
> 그리고 이러한 명령어는 우리의 기본 이미지에 포함된 명령어일 뿐입니다.

> [!cite]- **You can see here the individual sizes of each of the layers that are included, or that are created as a result of the commands in our base image.**  
> 여기에서 기본 이미지의 명령어로 인해 생성되거나 포함된 각 레이어의 개별 크기를 확인할 수 있습니다.

> [!cite]- **For us to visualize this even better, I looked for the node 22 Dockerfile and we have it open here.**  
> 이를 더욱 명확하게 시각화하기 위해 Node 22 Dockerfile을 찾아 열어 보았습니다.

> [!cite]- **If we scroll up a little bit, you'll see that this is Docker node 22 bookworm Dockerfile.**  
> 화면을 조금 위로 이동하면, 이것이 Docker Node 22 Bookworm Dockerfile임을 확인할 수 있습니다.

> [!cite]- **So this is the Dockerfile for node 22.**  
> 따라서 이것이 Node 22의 Dockerfile입니다.

> [!cite]- **And if you were to scroll down here and start reading the commands, we will see that this run group ad is actually reflected.**  
> 화면을 아래로 이동하여 명령어를 읽어 보면, `RUN groupadd` 명령어가 실제로 반영된 것을 확인할 수 있습니다.

> [!cite]- **Here.**  
> 여기에서요.

> [!cite]- **You see the run group ad, the group ID 1000 nodes.**  
> `RUN groupadd` 명령어와 그룹 ID 1000이 노드와 함께 표시됩니다.

> [!cite]- **Then we have the node version 22 4.0.**  
> 그다음에는 Node 버전 `22.4.0`이 있습니다.

> [!cite]- **This corresponds to this one here.**  
> 이것은 여기 표시된 것과 일치합니다.

> [!cite]- **Then we have a run command which corresponds to this run command.**  
> 그리고 `RUN` 명령어가 있으며, 이는 해당 `RUN` 명령어와 일치합니다.

> [!cite]- **So as you can see, each instruction in a Docker file creates a new layer in the final image.**  
> 따라서 보시는 것처럼, Docker 파일의 각 명령어는 최종 이미지에서 새로운 레이어를 생성합니다.

> [!cite]- **And you can also see this is very cool.**  
> 그리고 이 점이 매우 흥미롭습니다.

> [!cite]- **Which of these layers are actually contributing to the final size the most?**  
> 최종 이미지 크기에 가장 큰 영향을 미치는 레이어는 무엇일까요?

> [!cite]- **So if we were to look into our instructions, the things that we have control over, these are actually just adding roughly three megabytes to this whole size of 1.11GB.**  
> 우리가 제어할 수 있는 명령어를 살펴보면, 이는 전체 1.11GB 크기에 약 3MB만 추가하고 있습니다.

> [!cite]- **So there is very little optimization that we can do at our end in our files to improve the size of the image.**  
> 따라서 우리가 파일에서 이미지 크기를 최적화할 수 있는 부분은 매우 제한적입니다.

> [!cite]- **If we want to improve the size of this image, we would actually have to look at the layers that are coming from our base image.**  
> 이미지 크기를 개선하려면, 기본 이미지에서 생성된 레이어를 분석해야 합니다.

> [!cite]- **More specifically, primarily these two lines.**  
> 더 구체적으로는, 주로 이 두 줄입니다.

> [!cite]- **Here they are adding more than 700MB to this final image.**  
> 여기에서 최종 이미지 크기에 700MB 이상을 추가하고 있습니다.

> [!cite]- **And if we were to actually look into the Docker file, we will see that these lines, they happen before the first instruction.**  
> Docker 파일을 실제로 살펴보면, 이러한 줄이 첫 번째 명령어보다 먼저 발생함을 확인할 수 있습니다.

> [!cite]- **Right.**  
> 맞습니다.

> [!cite]- **So the first instruction that's coming from the Docker node or from the node 22 Docker file is this group add which is this instruction here.**  
> Docker Node 또는 Node 22 Docker 파일에서 처음 나오는 명령어는 `groupadd`이며, 바로 여기 있는 이 명령어입니다.

> [!cite]- **So these other instructions which are all starting with forward slash bin forward slash shell here they are actually coming from this base image here that is used in turn by the node 22 image, which we use as the base image.**  
> 그리고 `/bin/sh`로 시작하는 이러한 다른 명령어들은 사실 여기에서 사용된 기본 이미지에서 비롯된 것이며, 이는 Node 22 이미지에서 다시 사용되는 기본 이미지입니다.

> [!cite]- **As you can see here, it's kind of a quote unquote chaining of base images.**  
> 여기에서 볼 수 있듯이, 이는 일종의 "기본 이미지 연결(chain)"이라고 할 수 있습니다.

> [!cite]- **So this base image here is actually the biggest culprit when it comes to our large image size.**  
> 따라서 이 기본 이미지가 우리가 가진 대형 이미지 크기의 주된 원인입니다.

> [!cite]- **Great.**  
> 좋습니다.

> [!cite]- **I'm already getting a little bit ahead of myself because I'm touching upon topics or points of optimizing the image size here.**  
> 이미지를 최적화하는 부분에 대해 이야기하고 있어서 조금 앞서 나가고 있는 것 같네요.

> [!cite]- **But really the main message of this lecture is how the layered architecture of Docker enables us to really leverage all these intermediary commands here, because they actually map out to intermediary images.**  
> 하지만 이번 강의의 핵심 메시지는 Docker의 계층화된 아키텍처가 이러한 중간 명령어들을 활용할 수 있도록 해준다는 점입니다. 왜냐하면 이들은 실제로 중간 이미지에 매핑되기 때문입니다.

> [!cite]- **That means in terms of Docker, we can actually cache these intermediary images, right.**  
> 즉, Docker에서는 이러한 중간 이미지를 캐시할 수 있다는 뜻입니다, 맞죠?

> [!cite]- **So we can cache them and we can reuse them.**  
> 따라서 이를 캐시하고 다시 사용할 수 있습니다.

> [!cite]- **So if we have something that let's say up to here, everything is the same in a new Docker file.**  
> 즉, 여기까지 모든 내용이 동일한 새로운 Docker 파일이 있다고 가정해 봅시다.

> [!cite]- **And then we just change these commands here.**  
> 그리고 여기에서 일부 명령어만 변경한다고 가정하면,

> [!cite]- **Then Docker is able to cache and reuse all these upstream images here or all these upstream layers.**  
> 그러면 Docker는 이러한 모든 상위 이미지 또는 상위 레이어를 캐시하고 재사용할 수 있습니다.

> [!cite]- **And this is going to speed up the build time.**  
> 이는 빌드 시간을 더욱 단축시켜 줍니다.

> [!cite]- **This is the magic of Docker layered architecture.**  
> 이것이 바로 Docker 계층 아키텍처의 마법입니다.

> [!cite]- **It's a very interesting mechanism, very interesting system.**  
> 매우 흥미로운 메커니즘이며, 매우 흥미로운 시스템이죠.

> [!cite]- **But I believe that's enough for this lecture for us to understand how the different commands of a Docker file lead to different layers.**  
> 하지만 이번 강의에서는 Docker 파일의 다양한 명령어가 어떻게 서로 다른 레이어를 생성하는지 이해하는 것으로 충분할 것 같습니다.

> [!cite]- **Let's take a short break and come back in the next lecture.**  
> 잠시 쉬고 다음 강의에서 다시 이어가도록 합시다.
