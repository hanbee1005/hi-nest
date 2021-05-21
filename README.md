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
  