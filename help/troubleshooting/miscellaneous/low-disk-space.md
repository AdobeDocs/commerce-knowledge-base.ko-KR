---
title: 디스크 공간 부족
description: 이 문서에서는 클라우드 인프라에서 Adobe Commerce의 특정 환경에 대한 공간이 부족한 상황에 대한 해결 방법을 제안합니다.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# 디스크 공간 부족

이 문서에서는 클라우드 인프라에서 Adobe Commerce의 특정 환경에 대한 공간이 부족한 상황에 대한 해결 방법을 제안합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

쓰기 가능한 디렉터리가 있는 디스크의 디스크 공간이 부족합니다. 한 가지 증상은 [중단된 배포](https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26878)일 수 있습니다.

디스크 사용량을 확인하려면 다음 명령을 실행합니다.

```bash
df -h var/
```

## 원인

`var` 디렉터리는 일반적으로 많은 공간이 필요하고 쉽게 정리할 수 있는 디렉터리입니다.

Adobe Commerce은 모든 로그 파일을 `var` 디렉터리에 저장합니다. 새 로그 파일이 생성되며 이전 로그 파일은 매일 보관됩니다. 그러나 생성된 오류의 수가 계속 증가하면 로그 파일에 점점 더 많은 공간이 소요됩니다.

사용자 지정 가져오기/내보내기 파일도 `var` 디렉터리에 저장되며 숫자가 증가하면 공간을 차지합니다.

## 솔루션

솔루션 옵션:

* 큰 로그 파일이 있는지 확인하고 큰 이유를 조사하면 많은 로그 출력을 생성하는 문제를 수정하십시오.
* `var` 디렉터리를 정리합니다.
* `var` 디렉터리의 크기를 추적하고 정리하도록 크론 작업을 설정합니다.
* 사용하지 않은 디스크 공간이 있는 경우 더 많은 디스크 공간을 할당하십시오. (공간 제한 사항을 확인하는 방법에 대한 자세한 내용은 아래 섹션을 참조하십시오.)
   * 스타터 계획, 모든 환경 및 Pro 계획 통합 환경의 경우 [디스크 공간 관리: 디스크 공간 할당](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space)에 설명된 대로 사용하지 않는 디스크 공간이 있으면 디스크 공간을 할당할 수 있습니다.
   * Pro 플랜 스테이징 및 프로덕션 환경의 경우, 일부 사용하지 않은 디스크 공간이 있는 경우 지원 센터에 문의하여 더 많은 디스크 공간을 할당하십시오.
* 공간 제한에 도달했지만 여전히 공간 문제가 낮은 경우 더 많은 디스크 공간을 구입하는 것이 좋습니다. 자세한 내용은 Adobe 계정 팀에 문의하십시오.

### 디스크 공간 제한 확인

클라우드 인프라 환경의 각 Adobe Commerce에 대해 얼마나 많은 공간이 있는지 확인하려면:

1. [클라우드 콘솔](https://console.adobecommerce.com)에 로그인합니다.
1. **[!UICONTROL All projects]** 대시보드에서 관련 프로젝트를 선택합니다. 왼쪽 모서리에 디스크 공간 가용성이 표시됩니다.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
