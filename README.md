# Hi Nest!

Learning how to build Enterprise NodeJS applications using NestJS

## Architecture of NestJS
- main.ts에서 AppModule 실행으로 시작
- **Controllers**: url을 가져와서 메소드에 매핑하고 그에 맞는 메소드를 실행
- **Service**: 실제 비즈니스 로직 처리
- npm run start로 시작

## REST API
- controller
  + 'nest g co 컨트롤러이름' 명령어를 사용하여 controller 생성
  + REST API 애노테이션을 추가한 메소드 생성
    - **@Get**: read
    - **@Post**: create
    - **@Delete**: delete
    - **@Patch**: update, @Put은 전체 @Patch는 부분 업데이트
  + url path에 포함된 정보는 **@Param('정보명')** 애노테이션을 통해 받을 수 있음
  + HTTP Body에 포함된 정보는 **@Body** 애노테이션을 통해 받을 수 있음
  + query param으로 전달되는 정보는 **@Query('정보명')** 애노테이션을 통해 받을 수 있음
- service
  + 'nest g s 서비스이름' 명령어를 사용하여 service 생성
  + controller에서 service를 요청할 때는 생성자 메소드의 파라미터로 요청
    - ex) constructor(private readonly moviesService: MoviesService)
  + nest에서 제공하는 예외처리
    - throw NotFoundException();
    - throw 키워드를 사용하여 예외 발생
- validation
  + nest에서 제공하는 ValidationPipe를 사용
  + ValidationPipe 옵션
    - whilelist: true로 설정하면 유효성 검사 데코레이터를 사용하지 않는 속성의 유효성 검사 객체를 제거합니다.
    - forbidNonWhitelisted: true로 설정하면 화이트리스트에 없는 속성 검사 객체를 제거하는 대신 에러를 발생시킵니다.
    - transform: true로 설정하면 dto에 맞는 타입으로 자동 변환합니다.
  + 참고: https://docs.nestjs.com/techniques/validation

## UNIT TESTING
- jest: 자바스크립트를 쉽게 테스팅하는 npm 패키지로 .spec.ts 파일을 찾아서 테스트 수행
- UnitTest: 각각의 함수 단위 테스트
- e2e: End-to-End로 전체 흐름을 테스트
- 'npm run test:cov' 명령어로 어느정도 테스트가 진행되었는지 확인 가능
- 'npm run test:watch' 명령어로 테스트 코드를 작성하면서 테스트 성공 여부를 확인할 수 있음

## E2E TESTING
- 'npm run test:e2e' 명령어를 통해 test 디렉토리 아래 app.e2e-spec.ts를 테스트 할 수 있음
  