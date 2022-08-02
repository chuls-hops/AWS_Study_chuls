### EFS 사용시 참고할점 ###

1. VPC에 호스트이름을 활성화 한다. 
2. EFS생성시 사용할 AZ를 선택하고 각각 ENI의 SG에 NFS통신이 인바운드로 들어올수 있도록 설정해야 마운트가 가능하다. 
3. DNS가 동작하지 않더라도 ip로는 마운트가 가능하다. 
4. EFS 엔드포인트 노출시 가용 영역(AZ)당 탑재 대상은 한 개만 만들 수 있습니다.
- EC2 인스턴스 및 탑재 대상을 포함하는 VPC 3개 가용 영역과 마운트된 EFS 파일 시스템을 보여 주는 다이어그램입니다.
이 그림에서는 Amazon EFS 파일 시스템에 액세스하는 다른 VPC 서브넷에서 시작된 EC2 인스턴스 3개가 나와 있습니다. 또한 각 가용 영역의 서브넷 수와 관계없이 가용 영역마다 탑재 대상이 하나씩 있는 것을 알 수 있습니다. 

![image](https://docs.aws.amazon.com/ko_kr/efs/latest/ug/images/efs-manage-mount-targets.png)

