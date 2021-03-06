---

copyright:
  years: 2017
lastupdated: "2017-08-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# FAQ

이 절에는 IBM Bluemix Load Balancer 서비스에 대해 일부 자주 묻는 질문의 응답이 포함되어 있습니다. 

## 내 로드 밸런서 서비스를 사용하여 정의할 수 있는 최대 가상 포트는 몇 개입니까? 

새 로드 밸런서 서비스를 작성하면서 최대 두 개의 가상 포트를 정의할 수 있습니다. 서비스가 작성된 후에는 추가 가상 포트를 정의할 수 있습니다. 허용되는 최대 가상 포트 수는 10입니다.  

## 내 로드 밸런서와 연관시킬 수 있는 최대 컴퓨팅 인스턴스는 몇 개입니까?

50개입니다.

## 내부 클라이언트로만 액세스할 수 있는 내부 전용의 개인용 로드 밸런서를 작성할 수 있습니까?   

현재는 불가능합니다. IBM Bluemix Load Balancer에 호스팅된 서비스는 공용 인터넷에서 액세스할 수 있는 완전한 도메인 이름으로 지정됩니다.  

## 여러 상태 검사 매개변수에 대한 기본 설정 및 허용된 값은 무엇입니까? 

기본 설정 및 허용된 값은 다음과 같습니다. 

* **상태 검사 간격:** 기본값은 5초이고, 범위는 2 – 60초입니다. 
* **상태 검사 응답 제한시간:** 기본값은 2초이고, 범위는 1 – 59초입니다.
* **최대 재시도:** 기본값은 2회의 재시도이고, 범위는 1 – 10회입니다. 

**참고:** 상태 검사 응답 제한시간은 항상 상태 검사 간격 값 미만으로 설정되어야 합니다.  

## 이 서비스를 사용하여 원격 데이터 센터에 상주하는 컴퓨팅 인스턴스를 사용할 수 있습니까? 

로드 밸런서 서비스 및 컴퓨팅 인스턴스는 동일한 데이터 센터 내에 로컬로 상주하는 것이 좋습니다. 로드 밸런서 서비스의 그래픽 인스턴스(GUI)는 기타 원격 데이터 센터의 컴퓨팅 인스턴스를 표시하지 않습니다. 그러나 GUI에는 동일한 도시에 있는 기타 데이터 센터(예: `DALxx`와 같이 이름에서 첫 세 자의 문자를 공유하는 데이터 센터)의 컴퓨팅 인스턴스가 포함됩니다. API 인터페이스를 사용하여 원격 데이터 센터에서 컴퓨팅 인스턴스를 추가할 수 있습니다.  

## SSL 오프로드를 사용하여 지원되는 TLS 버전은 무엇입니까? 어떤 암호가 지원됩니까? 

Bluemix Load Balancer 서비스는 TLS 1.2 및 SSL 종료를 지원합니다.  

다음은 지원되는 암호에 대한 목록 세부사항입니다(우선순위에 따라 나열됨).   

* ECDHE-RSA-AES256-GCM-SHA384 
* ECDHE-RSA-AES256-SHA384 
* DHE-RSA-AES256-GCM-SHA384 
* DHE-RSA-AES256-SHA256 
* AES256-GCM-SHA384 
* AES256-SHA256 
* ECDHE-RSA-AES128-GCM-SHA256 
* ECDHE-RSA-AES128-SHA256 
* DHE-RSA-AES128-GCM-SHA256 
* DHE-RSA-AES128-SHA256 
* AES128-GCM-SHA256 
* AES128-SHA256 

## 내 SSL 암호 목록을 사용자 정의할 수 있습니까? 

현재는 불가능합니다. 

## 내 계정으로 작성할 수 있는 최대 로드 밸런서 서비스 인스턴스는 몇 개입니까?  

현재 최대 20개의 서비스 인스턴스를 작성할 수 있습니다. 더 많은 인스턴스가 필요하면 IBM 지원 센터에 문의하십시오.  


