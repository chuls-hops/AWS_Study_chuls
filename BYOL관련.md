### MS라이선스 관련
- MS라이선스의 경우 EA용 라이선스일 경우에 BYOL로 확용이 가능하나 Windows 서버의 경우 Dedicated Host 상품 형태에서만 사용이 가능함. 



#### 아래 원문 참고



### AWS에서 Microsoft라이센스 BYOL로 사용하기
 

#### AWS에서 Microsoft 라이센스를 사용하기 위해서는 License Mobility 를 이해하셔야 합니다.

 

- License Mobility란?

#### AWS에서 Microsoft 라이센스 유동적으로 사용할 수 있게 허용해준 정책입니다.

 

- License Mobility를 적용받아 Microsoft 라이센스를 AWS사용 할 수 있는 대상은?

#### Microsoft Volume License 보유 고객 중 Microsoft Software Assurance(SA) 계약을 적용 받는 고객입니다.

#### 또한, 유효한 라이센스인지 Software Assurance계약이 포함되어 있는지 Microsoft로 부터 승인을 받아야 합니다. 

#### 승인 절차는 다음 URL을 통해서 진행하시면 됩니다.

 #### https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-license-mobility.aspx

 

- Microsoft License는 있는데 꼭 SA계약과 인증이 필요할까요?

#### 결론부터 말씀드리자면 아닙니다.

#### SA계약과 인증이 없어도 아래와 같은 제약 조건으로  Microsoft License를 BYOL로 사용할 수 있습니다.

#### 또, SA계약이 있어도 사용할 수 있는 Microsoft 제품에는 종류가 정해져있으니 잘 확인해야합니다.

 

### 1) Microsoft License가 있는데, SA(software assurance) 계약이 안되어있는 경우 ( --> Dedicated host 사용)

#### EC2 생성은 Dedicated host로 사용해야함
#### BYOL로 사용하기 위해 AWS vm import로 EC2 생성을 해야 함
#### 대표적인 MS제품 중 windows server / MS SQL server 둘 다 해당 됨
 

###  2) Microsoft License는 있는데, SA(software assurance) 계약이 되어 있는 경우 ( --> Default tenancy 사용)

EC2 생성은 일반(Default tenancy)타입으로 사용 가능함
MS에 양식을 작성하여 AWS License Mobility인증을 받아야함
BYOL로 사용하기 위해 AWS vm import로 EC2 생성을 해야 함
대표적인 MS제품 중 MS SQL server가 해당하며 Windows server는 SA적용 대상이 아님
즉, windows server를 BYOL로 사용하는 방법은 1)번 Dedicated host를 사용 밖에 없음
 

* SA계약에 적용되는 MicroSoftware제품 목록은?

(주의 : Windows server는 적용 대상이 아님)

Exchange Server
SharePoint Server
SQL Server Standard Edition
SQL Server Enterprise Edition
SQL Server Business Intelligence Edition
Skype for Business Server
System Center Server
Dynamics CRM Server
Dynamics AX Server
Project Server
Visual Studio Team Foundation Server
BizTalk Server
Forefront Identity Manager
Forefront Unified Access Gateway
Remote Desktop Services

 

* AWS VM import란 ?

 MS제품이 설치된 VM image(VMDK)를 s3로 전송 후 AMI로 변경 하는 작업(vm이미지생성 , s3 전송, AMI변경 시간소요 고려 필요)

 

* Dedicated Host란? 

Amazon EC2 전용 호스트는 고객 전용의 EC2 인스턴스 용량을 갖춘 물리적 서버입니다. 전용 호스트를 사용하면 기존 서버에 한정된 소프트웨어 라이선스를 사용할 수 있으므로 규정 준수 요구 사항을 해결하면서 비용도 절감할 수 있습니다. 단, Dedicated Host는 서버의 묶음으로 구매해야하므로 최소 구매 단위를 확인해야합니다.

 

이상 AWS에서 Microsoft라이센스 BYOL로 사용하는 방법을 설명 드렸습니다.

 

 

* 참고 AWS URL : https://aws.amazon.com/ko/windows/resources/licensemobility/


#### 원문출처 https://support.xavis.kr/hc/ko/articles/360029023232-AWS%EC%97%90%EC%84%9C-Microsoft%EB%9D%BC%EC%9D%B4%EC%84%BC%EC%8A%A4-BYOL%EB%A1%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0
