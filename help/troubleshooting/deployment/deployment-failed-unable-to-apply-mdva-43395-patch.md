---
title: '배포 실패: MDVA-43395 패치를 적용할 수 없음'
description: 이 문서에서는 MDVA-43395 패치를 적용하려고 하면 배포가 실패하는 문제에 대한 해결 방법을 제공합니다.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 배포 실패: MDVA-43395 패치를 적용할 수 없음

이 문서에서는 MDVA-43395 패치를 적용하려고 하면 배포가 실패하는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce(모든 버전)

## 문제

MDVA-43395 패치를 적용할 수 없습니다.

## 원인

이미 패치가 포함된 [magento/magento-cloud-patches 1.0.16](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016)이(가) 설치되어 있는 경우 클라우드 판매자는 MDVA-43395 패치를 별도로 적용할 필요가 없습니다.

## 솔루션

이 문제를 해결하려면 `m2-hotfixes` 디렉터리에서 MDVA-43395 및 MDVA-43443 패치를 제거하고 다시 배포하십시오.

`m2-hotfixes` 디렉터리를 통해 MDVA-43443 패치를 적용할 수 있는 경우 위에 언급된 대로 해당 패치를 제거해야 합니다. 이후 버전의 Adobe Commerce에는 이러한 패치가 이미 포함되어 있으므로 나중에 업그레이드하면 배포가 실패할 수 있습니다.

패치가 적용되었는지 확인하려면 `vendor/bin/magento-patches -n status |grep 43443` 명령을 실행하십시오.
이렇게 여러 개의 결과가 표시되면 `m2-hotfixes` 폴더에서 MDVA-43443 패치를 제거해야 합니다.

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## 관련 읽기

* 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
* 개발자 설명서에서 [Commerce용 클라우드 패치](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016)
