### ECS관련 정리
1. public subnet, private subnet 각각 2개를 구성 
2. ECS 클러스터를 Private subnet에 배포
3. 클러스터를 생성할때 SG가 연결된다. IAM Role도 자동으로 생성이 된다, Cloud Watch logs도 활성화 시킬수 있다. 
4. Cloud Watch logs가 동작하려면 자동으로 생성된 IAM Role에 CloudWatchAccessFull 권한을 넣어주어야 한다. 
5. 서비스를 구성하려면 "작업정의"를 통해 작업정의를 생성하여야 한다. 
6. 작업정의를 할때 컨테이미지 레지스트리 주소가 필요하다. 이때 ECR을 사용하면 간편한데 확인해보면 ECS클러스터 생성할때 생긴 IAM Role에 ECR 권한이 들어가 있다. 
7. 그래서 별도 권한 설정없이 접근이 잘 된다. 
8. EC2 타입의 클러스터를 만들어 두더라도 Fargate를 통해 작업정의하고 서비스를 생성할수 있다. 
9. ECS 서비스를 노출 시키기 위해서는 ALB생성이 필요하다 
10. ALB를 생성하기 위해서는 Target Group이 있어야 생성이 된다. 
11. Target Group을 생성할때 인스턴스 타입으로 연결 해놓으면 된다. 
12. 인스턴스 타입으로 연결한 Target Group은 NLB에서 사용할수 없다. NLB는 ip 타입으로 연결한 tg만 사용할 수 있다. 
13. ALB는 보통 public subnet에 구성하면 되고 경로 설정을 해주면 된다. 
14. ECS클러스터에 작업정의, ALB가 생성 되었다면 이제 서비스를 생성하면 서비스 노출이 된다. 
15. 서비스 생성시 기존에 만들어둔 작업정의와 ALB를 사용하면된다. 
16. 온프렘과 연동 및 고정아이피 요건을 위해 Internal NLB를 사용하는데 target group을 ALB로 지정할수 있는데, 이때 internal, internet-facing 타입 ALB모두 설정이 된다. 
17. EC2를 private 존에 생성하고 해당 private 라우팅 테이블에 외부로 갈수 있는 경로를 삭제 해버렸다. 이때도 internal nlb -> internet-facing ALB로 트래픽 전달이 되는지 확인 하니 페이지가 정상적으로 호출이 되었다.
