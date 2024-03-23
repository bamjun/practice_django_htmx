[깃링크](https://github.com/andyjud/django-starter-assets)  


https://youtu.be/SQ4A7Q6_md8?t=799



--- 
# &darr; learned  

## 1. mkdir -p
`mkdir` 명령어는 유닉스 및 유닉스 계열 시스템에서 새 디렉토리(폴더)를 만드는 데 사용됩니다. 여기서 `-p` 옵션은 "parents"의 약자로, 지정된 디렉토리와 필요한 모든 상위 디렉토리를 함께 생성하는 역할을 합니다. 즉, 주어진 경로에 있는 중간 디렉토리가 없으면 `-p` 옵션을 사용하면 그 중간 디렉토리들도 모두 생성됩니다.

예를 들어, 다음 명령어를 실행한다고 가정해 봅시다:

```sh
mkdir -p /home/user/docs/newfolder
```

이 경우, `/home/user/docs` 경로가 아직 존재하지 않으면, `mkdir -p` 명령어는 `newfolder`와 함께 필요한 `/home`, `/home/user`, `/home/user/docs` 디렉토리를 모두 생성합니다. 이미 해당 경로가 존재하면 추가적인 에러 메시지 없이 무시하고 새로 지정된 디렉토리만을 생성합니다.

`-p` 옵션은 스크립트를 작성할 때 특히 유용하며, 디렉토리 구조를 프로그램적으로 생성할 때 필요한 디렉토리가 이미 있는지 확인할 필요 없이 바로 생성할 수 있게 해줍니다.

---