---
title: CLI에서 DDoS 공격 확인
description: 이 문서에서는 서버의 명령줄 인터페이스(CLI)에서 DDoS(Distributed Denial of Service) 공격을 확인하는 방법에 대해 설명합니다.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# CLI에서 DDoS 공격 확인

이 문서에서는 서버의 명령줄 인터페이스(CLI)에서 DDoS(Distributed Denial of Service) 공격을 확인하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce, 모든 버전
* Magento Open Source, 모든 버전

## 문제

웹 사이트가 느리고 잠재적인 DDoS 공격을 확인하기 위해 CLI 이외의 다른 분석 애플리케이션 도구에 액세스할 권한이 없습니다. DDoS 공격의 증상은 네트워크 구성, 사용하는 소프트웨어 등에 따라 크게 달라질 수 있습니다.

그러나 DDoS 공격을 식별하는 데 도움이 되도록 특별히 설계된 분석 소프트웨어 제품을 사용하는 것이 좋습니다.

## 원인

웹 사이트가 느려지는 원인은 성능이 느린 서버, 높은 CPU 사용량 또는 스크립트, 코드 또는 저렴한 하드웨어의 잘못된 구성 등 여러 가지가 있습니다. 때로는 DDoS 공격 때문일 수 있습니다. DDoS 공격을 확인해야 하는 기본 툴 중 두 가지는 Adobe Commerce 로그와 CLI입니다.

DDoS 공격을 파악하기 위해 특별히 고안된 소프트웨어를 사용하는 것이 조사에 매우 유용할 것이라는 점을 다시 한 번 주목해야 합니다.

## 솔루션 단계

1. Adobe Commerce 로그를 확인하여 DDoS 공격 이외의 다른 상황이 발생하고 있는지 확인합니다. 자세한 내용은 개발자 설명서에서 다음 문서를 참조하십시오.
   * [Adobe Commerce 및 Magento Open Source 로그 위치](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/cli/enable-logging)
   * [클라우드 인프라의 Adobe Commerce 로그 위치](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/test/log-locations)
1. CLI를 사용하여 `netstat` 명령을 사용하여 현재 모든 인터넷 연결을 확인하세요. `netstat -na`. 서버에 대해 설정된 모든 활성 연결이 표시됩니다. 여기에서 동일한 IP 주소에서 너무 많은 연결이 발생하는 것을 볼 수 있습니다.
1. 한 IP 주소 또는 IP 주소 그룹에서 너무 많은 연결을 정렬 및 인식할 수 있도록 설정된 연결 결과를 포트 80(웹 사이트의 HTTP 포트)에 연결된 연결로만 좁히려면 `netstat -an | grep :80 | sort` 명령을 사용합니다. 포트 443에서 https에 대해 동일한 명령을 반복할 수 있습니다. `netstat -an | grep :443 | sort`. 또 다른 옵션은 원래 명령을 포트 80과 443 둘 다로 확장하는 것입니다. `netstat -an | egrep ":80|:443" | sort`.
1. 서버에서 많은 활성 `SYNC_REC`이(가) 발생하고 있는지 확인하려면 다음 명령을 사용합니다.     `netstat -n -p|grep SYN_REC | wc -l`     이 수치는 일반적으로 5보다 작지만 DDoS 공격의 경우 훨씬 높을 수 있지만, 일부 서버의 경우 일반적인 상태일 수 있습니다.
1. `SYNC_REC` 상태를 보내는 모든 IP 주소를 나열하려면 `netstat -n -p | grep SYN_REC | sort -u` 명령을 사용합니다.
1. `SYNC_REC` 상태를 보내는 모든 고유 IP 주소를 추가로 나열하려면 `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’` 명령을 사용하십시오.
1. `netstat` 명령을 사용하여 각 IP 주소가 서버에 대해 수행하는 연결 수를 계산하고 계산할 수도 있습니다. `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. 서버에 연결된 UDP 또는 TCP 프로토콜 연결 수를 나열하려면 `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n` 명령을 사용합니다.
1. 모든 연결 대신 설정된 연결을 확인하고 각 IP 주소의 연결 수를 표시하려면 `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr` 명령을 사용합니다.
1. 포트 80에 대해 IP 주소별로 나열된 연결 수를 표시하려면 `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1` 명령을 사용합니다.

실제로 DDoS 공격을 받고 있는지 확인하기 위해 찾은 데이터에 적절한 분석을 제공할 사람이 있는지 확인하십시오. 위의 단계에서 서버 CLI의 `netstat` 명령을 사용하면 DDoS 공격이 발생했는지 분석하는 데 도움이 되지만, 적절한 분석과 함께 DDoS 공격을 식별하도록 특별히 설계된 소프트웨어 분석 제품을 사용하는 것이 DDoS 위협을 식별하는 데 가장 좋은 도구입니다.

DDoS 공격을 받고 있는 경우, 네트워크 구성 및 DDoS 공격이 발생하는 방식에 따라 수행할 수 있는 단계가 다르지만, 일반적인 조언은 ISP에 문의하고 서버의 새 IP 주소를 얻거나 DDoS 문제를 처리하는 데 숙련된 IT 전문가에게 문의하여 특정 상황을 분석하고 조언하는 것입니다.

## 개발자 설명서의 관련 내용:

* [DDoS 보호](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/fastly#ddos-protection)
* [CLI 명령 사용](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli)
* [Commerce용 Cloud CLI](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)
