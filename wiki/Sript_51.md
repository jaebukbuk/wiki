> [!cite]- **Hello and welcome back.**  
> 안녕하세요, 다시 만나서 반갑습니다.

> [!cite]- **In this lecture I would like to discuss how to use Docker ignore files to help us also exclude some of the files that we do not want to upload as the build context to the docker host.**  
> 이번 강의에서는 Docker ignore 파일을 사용하여 빌드 컨텍스트로 도커 호스트에 업로드하고 싶지 않은 일부 파일을 제외하는 방법에 대해 논의하고자 합니다.

> [!cite]- **We have already discussed that one way for us to avoid uploading unwanted files is to be very specific regarding what we are copying from, for example, from our local folder into our container.**  
> 우리는 이미 불필요한 파일의 업로드를 피하는 한 가지 방법으로, 로컬 폴더에서 컨테이너로 복사하는 내용을 매우 구체적으로 지정하는 방법을 논의했습니다.

> [!cite]- **However, this is often not very practical.**  
> 그러나 이는 종종 실용적이지 않습니다.

> [!cite]- **So let's go to the IDE and try to just create a small project here that will be similar to what you will actually see in real life.**  
> 그래서 IDE로 이동하여 실제로 접할 수 있는 것과 유사한 작은 프로젝트를 생성해 보겠습니다.

> [!cite]- **So we have something like this.**  
> 이렇게 구성되어 있습니다.

> [!cite]- **Here we have an index.js.**  
> 여기에 `index.js` 파일이 있습니다.

> [!cite]- **So let's change a few things.**  
> 몇 가지를 변경해 봅시다.

> [!cite]- **Let's create a source folder.**  
> `source` 폴더를 생성해 봅시다.

> [!cite]- **And then within this source folder we will say something like component one for example component one.**  
> 그리고 이 `source` 폴더 안에 `component_one` 같은 폴더를 만듭니다.

> [!cite]- **And then here we will have let's say the component one dot js.**  
> 그리고 여기에 `component_one.js` 파일을 생성합니다.

> [!cite]- **Yes.**  
> 네.

> [!cite]- **And then we'll also have something like a test file component one for example dot test dot js.**  
> 그리고 테스트 파일로 `component_one.test.js` 같은 파일도 생성합니다.

> [!cite]- **Right.**  
> 맞습니다.

> [!cite]- **So this is one example of a file test file that we would probably not need to actually build our final Docker container or Docker image.**  
> 이 파일은 최종 Docker 컨테이너 또는 Docker 이미지 빌드에 필요하지 않은 테스트 파일의 한 예입니다.

> [!cite]- **This is necessary for CI, CD and for local development so that we can run the tests.**  
> 이 파일은 CI/CD 및 로컬 개발을 위해 필요하며, 테스트를 실행하기 위한 것입니다.

> [!cite]- **However we don't need to include test files in our final Docker image.**  
> 그러나 최종 Docker 이미지에는 테스트 파일을 포함할 필요가 없습니다.

> [!cite]- **So we have here source component one.**  
> 따라서 `source/component_one` 폴더가 구성되었습니다.

> [!cite]- **We're also going to have a new file here.**  
> 그리고 새로운 파일을 추가할 예정입니다.

> [!cite]- **Let's say this index dot js for example.**  
> `index.js` 파일을 예로 들어 봅시다.

> [!cite]- **And this is going to just have the the content of our index dot JS here.**  
> 이 파일에는 `index.js`의 내용을 포함할 것입니다.
> [!cite]- **Right.**  
> 맞습니다.

> [!cite]- **So this is one example of a file test file that we would probably not need to actually build our final Docker container or Docker image.**  
> 이것은 최종 Docker 컨테이너 또는 Docker 이미지를 빌드하는 데 필요하지 않은 테스트 파일의 한 예입니다.

> [!cite]- **This is necessary for CI, CD and for local development so that we can run the tests.**  
> 이 파일은 CI/CD 및 로컬 개발을 위해 필요하며, 테스트 실행을 위한 것입니다.

> [!cite]- **However we don't need to include test files in our final Docker image.**  
> 그러나 최종 Docker 이미지에는 테스트 파일을 포함할 필요가 없습니다.

> [!cite]- **So we have here source component one.**  
> 따라서 `source/component_one` 폴더가 구성되었습니다.

> [!cite]- **We're also going to have a new file here.**  
> 그리고 새로운 파일을 추가할 예정입니다.

> [!cite]- **Let's say this index dot js for example.**  
> `index.js` 파일을 예로 들어 봅시다.

> [!cite]- **And this is going to just have the the content of our index dot JS here.**  
> 이 파일에는 `index.js`의 내용을 포함할 것입니다.

> [!cite]- **So let's just delete the one at the root of the directory.**  
> 그래서 루트 디렉터리에 있는 기존 파일을 삭제하겠습니다.

> [!cite]- **So we have something called source component one component one dot js component one Test.js.**  
> 따라서 `source/component_one` 폴더 안에 `component_one.js`와 `component_one.test.js`가 있습니다.

> [!cite]- **And then we also have here let's say component two for example.**  
> 그리고 `component_two` 폴더도 추가하겠습니다.

> [!cite]- **And the component two will actually have the files let's say component two Here js and component two dot test dot js.**  
> `component_two` 폴더에는 `component_two.js`와 `component_two.test.js` 파일이 들어갑니다.

> [!cite]- **And we could also have maybe we could make copies here and say component to copy.**  
> 또한 복사본을 만들어 `component_two_copy` 폴더를 생성할 수도 있습니다.

> [!cite]- **And then here this is going to be component to copy dot test dot JS.**  
> 그리고 여기에 `component_two_copy.test.js` 파일을 추가합니다.

> [!cite]- **Right.**  
> 맞습니다.

> [!cite]- **So we start having many many files.**  
> 이렇게 하면 파일이 점점 많아집니다.

> [!cite]- **And we actually want to exclude some of these files that are deeply nested here.**  
> 그리고 여기 깊숙이 위치한 일부 파일을 제외하고 싶습니다.

> [!cite]- **Or perhaps we also have some dependencies or many directories here.**  
> 또는 여러 개의 의존성 파일과 디렉터리가 있을 수도 있습니다.

> [!cite]- **And we don't want to specify everything in the Docker file.**  
> 그리고 모든 것을 Docker 파일에서 하나하나 지정하고 싶지는 않습니다.

> [!cite]- **Right.**  
> 맞습니다.

> [!cite]- **So this is not really practical to say copy source forward slash component one, forward slash component one, component one dot js.**  
> `source/component_one/component_one.js`를 개별적으로 복사하는 것은 실용적이지 않습니다.

> [!cite]- **And we're going to copy this into exactly the same thing here.**  
> 그리고 동일한 경로로 복사할 예정입니다.

> [!cite]- **And then we're going to have another line which is going to be for the component two for example, and then another line for the component to copy and so on and so forth.**  
> 그런 다음 `component_two`, `component_two_copy` 등을 개별적으로 복사하는 또 다른 줄을 추가해야 합니다.

> [!cite]- **So this is just not feasible.**  
> 이러한 방식은 비효율적입니다.

> [!cite]- **So we would actually like to just say please copy everything into our current.**  
> 그래서 현재 디렉터리의 모든 내용을 복사하고 싶습니다.

> [!cite]- **So basically just mirror the current directory structure into our container.**  
> 즉, 현재 디렉터리 구조를 컨테이너에 그대로 반영합니다.

> [!cite]- **And this is going to make the Dockerfile simpler.**  
> 이 방법은 Dockerfile을 더 단순하게 만듭니다.

> [!cite]- **However, we will run into the problem that we will copy these files, the test files as well as this some large file.**  
> 그러나 이렇게 하면 테스트 파일과 `some_large_file` 같은 불필요한 파일도 복사하게 되는 문제가 발생합니다.

> [!cite]- **Here we could tackle the some large file, for example by saying just copy the source folder.**  
> `source` 폴더만 복사하도록 설정하면 `some_large_file` 문제를 해결할 수 있습니다.

> [!cite]- **But this still does not solve the problem of copying these test files.**  
> 그러나 테스트 파일을 복사하는 문제는 여전히 남아 있습니다.

> [!cite]- **So one way for us to tackle everything at once is to create something called a dot docker ignore file and the docker ignore file.**  
> 이 문제를 한 번에 해결하는 방법은 `.dockerignore` 파일을 생성하는 것입니다.

> [!cite]- **It allows us to specify a series of paths, a series of files and directories, and possibly also extensions here that we wish to ignore.**  
> `.dockerignore` 파일을 사용하면 무시하고 싶은 경로, 파일, 디렉터리, 확장자를 지정할 수 있습니다.

> [!cite]- **So let's just do that here.**  
> 그럼 이제 `.dockerignore` 파일을 만들어 보겠습니다.

> [!cite]- **We're going to specify.**  
> 우리는 다음 내용을 지정할 것입니다.

> [!cite]- **The first one that we want to ignore is actually the some dash large Dash file.**  
> 첫 번째로 무시할 파일은 `some-large-file`입니다.

> [!cite]- **And so this here is the some large file here.**  
> 즉, `some_large_file`을 제외할 것입니다.

> [!cite]- **And the second pattern that we want to ignore is any file in any recursive directory here that ends in a test dot js extension.**  
> 두 번째로 제외할 패턴은 모든 하위 디렉터리에서 `test.js` 확장자로 끝나는 파일입니다.

> [!cite]- **So here we'll simply skip the test file.**  
> 여기에서 테스트 파일을 단순히 제외할 것입니다.

> [!cite]- **So we're not going to copy them into our final image.**  
> 따라서 우리는 이를 최종 이미지에 복사하지 않을 것입니다.

> [!cite]- **And we'll also skip the some large file.**  
> 그리고 `some_large_file`도 제외할 것입니다.

> [!cite]- **That's great.**  
> 좋습니다.

> [!cite]- **So we have written our dockerignore.**  
> 이제 `.dockerignore` 파일을 작성했습니다.

> [!cite]- **Let's see how this works.**  
> 이제 이것이 어떻게 작동하는지 확인해 봅시다.

> [!cite]- **Back in the terminal.**  
> 터미널로 돌아갑니다.

> [!cite]- **In the terminal we would like to now issue the command docker build once again.**  
> 터미널에서 다시 `docker build` 명령을 실행할 것입니다.

> [!cite]- **And I'm just going to copy the previous one here.**  
> 그리고 이전 명령을 복사할 것입니다.

> [!cite]- **And I'm going to enforce or I'm going to inform the whole context here.**  
> 그리고 전체 컨텍스트를 지정할 것입니다.

> [!cite]- **Let's press enter.**  
> Enter 키를 누릅니다.

> [!cite]- **And let's wait here.**  
> 그리고 잠시 기다립니다.

> [!cite]- **You will see that we have also transferred slightly bigger context because we have more files here.**  
> 여기에 파일이 더 많아졌기 때문에 전송된 컨텍스트가 다소 커진 것을 확인할 수 있습니다.

> [!cite]- **But we successfully ignored the some large file.**  
> 그러나 `some_large_file`을 성공적으로 제외했습니다.

> [!cite]- **Right.**  
> 맞습니다.

> [!cite]- **So if we look at the Docker file here docker file, we will see that we should potentially be copying that file because you're copying the whole contents of the directory.**  
> Docker 파일을 확인하면 전체 디렉터리의 내용을 복사하기 때문에 이 파일도 복사될 가능성이 있음을 알 수 있습니다.

> [!cite]- **However, whenever we build the image, that file was ignored.**  
> 그러나 이미지를 빌드할 때 해당 파일은 무시되었습니다.

> [!cite]- **And if we were to run Docker images once again here we will see that we have also a very small image.**  
> 그리고 `docker images` 명령을 다시 실행하면 아주 작은 이미지가 생성된 것을 확인할 수 있습니다.

> [!cite]- **Amazing.**  
> 놀랍습니다.

> [!cite]- **Now how about the test files?**  
> 그렇다면 테스트 파일은 어떻게 되었을까요?

> [!cite]- **Were they ignored?**  
> 제외되었을까요?

> [!cite]- **One way for us to find out is to actually run a shell in a container that we will run based on this image here.**  
> 이를 확인하는 한 가지 방법은 이 이미지를 기반으로 컨테이너를 실행하여 쉘을 여는 것입니다.

> [!cite]- **So if you are just interested in exploring the file system of an image, let's copy this image ID.**  
> 이미지의 파일 시스템을 탐색하고 싶다면 이 이미지 ID를 복사합니다.

> [!cite]- **Let's clear the console here and we'll simply run a docker run.**  
> 콘솔을 정리한 후 `docker run` 명령을 실행하겠습니다.

> [!cite]- **We can also add dash dash rm as a flag here so the container gets removed the moment we exit the container and it doesn't stay in our machine, it doesn't continue to consume some space.**  
> `--rm` 플래그를 추가하면 컨테이너를 종료하는 즉시 삭제되어 시스템에 남지 않고 공간을 계속 차지하지 않도록 할 수 있습니다.

> [!cite]- **So we will run dash it similar to the exact one.**  
> 따라서 `-it` 옵션을 사용하여 실행할 것입니다.

> [!cite]- **We're going to pass the image ID, and the name of the command that we want to execute is just a shell.**  
> 이미지 ID를 전달하고 실행할 명령은 단순히 쉘입니다.

> [!cite]- **In a moment we do that, we actually get a shell running inside of the forward slash app directory.**  
> 이 명령을 실행하면 `/app` 디렉터리 내부에서 쉘이 실행됩니다.

> [!cite]- **What we have just done here is we have overwritten the default cmd instruction that we have specified in our Dockerfile.**  
> 이렇게 하면 Dockerfile에서 지정한 기본 `CMD` 명령을 덮어쓰게 됩니다.

> [!cite]- **In our Dockerfile we have this command instruction the CMD instruction.**  
> 우리의 Dockerfile에는 `CMD` 명령이 포함되어 있습니다.

> [!cite]- **Here.**  
> 여기 있습니다.

> [!cite]- **However, we can override this by passing a new instruction here.**  
> 그러나 새로운 명령을 전달하여 이를 덮어쓸 수 있습니다.

> [!cite]- **We're going to come back to this topic a little bit later on in the course.**  
> 이 주제는 이후 강의에서 다시 다룰 예정입니다.

> [!cite]- **I just wanted to already get a shell here.**  
> 여기에서 먼저 쉘을 실행하고 싶었습니다.

> [!cite]- **So why not introduce this concept right.**  
> 그래서 이 개념을 소개해 보는 것도 좋겠습니다.

> [!cite]- **So first time we're seeing this concept, just keep that in the back of your mind.**  
> 이 개념을 처음 접하는 것이므로 기억해 두세요.

> [!cite]- **We're going to discuss it once again.**  
> 이 내용은 다시 논의할 예정입니다.

> [!cite]- **So now we have this here.**  
> 그래서 이제 실행되었습니다.

> [!cite]- **And we can actually list the contents.**  
> 그리고 실제로 콘텐츠를 확인할 수 있습니다.

> [!cite]- **You can see that actually the Dockerfile was copied here.**  
> Dockerfile이 여기 복사된 것을 확인할 수 있습니다.

> [!cite]- **But if you were to change into source and list here let's go into component one.**  
> `source` 디렉터리로 이동하여 목록을 보면 `component_one` 폴더가 보입니다.

> [!cite]- **Component one like so.**  
> `component_one` 폴더로 이동합니다.

> [!cite]- **And if we were to list here you will see that we do not have any test files.**  
> 여기에서 목록을 확인하면 테스트 파일이 없다는 것을 알 수 있습니다.

> [!cite]- **If we were to come back and go to component two here and want to list the files once again, then once again, no test files.**  
> `component_two` 폴더로 이동하여 파일 목록을 확인해도 테스트 파일이 없습니다.

> [!cite]- **So we have successfully managed to exclude files recursively within our project structure.**  
> 따라서 프로젝트 구조 내에서 파일을 성공적으로 재귀적으로 제외했습니다.

> [!cite]- **And to achieve that within the Docker file might actually have been a lot of effort.**  
> Dockerfile에서 이를 설정하는 것은 많은 노력이 필요했을 수도 있습니다.

> [!cite]- **Once again, we are working with a very simple project structure here.**  
> 여기에서는 매우 간단한 프로젝트 구조를 사용하고 있습니다.

> [!cite]- **So it might be the case that in real life this is considerably more complex.**  
> 실제 프로젝트에서는 훨씬 더 복잡할 가능성이 있습니다.

> [!cite]- **And there are a few different patterns that you wish to ignore here and to codify them in the Docker file, you might end up with a lot of copy instructions or some very confusing instructions here.**  
> 제외하고 싶은 여러 패턴이 있을 수 있으며, 이를 Dockerfile에 명시하면 복잡한 `COPY` 명령이 많아질 수 있습니다.

> [!cite]- **So the docker file is one way for us to actually programmatically skip copying some of the files in our folder and uploading them as part of the build context.**  
> Dockerfile은 특정 파일을 복사하지 않도록 프로그래밍적으로 설정하여 빌드 컨텍스트의 일부로 업로드하지 않는 한 가지 방법입니다.

> [!cite]- **Awesome.**  
> 멋집니다.

> [!cite]- **That's what I wanted to discuss with you in this lecture.**  
> 이 강의에서 다루고 싶었던 내용이 바로 이것입니다.

> [!cite]- **Let's then take a short break and come back in the next one.**  
> 잠시 쉬었다가 다음 강의에서 다시 시작하겠습니다.

이 방식으로 번역을 제공합니다. 추가 번역이 필요하면 언제든지 알려주세요! 😊