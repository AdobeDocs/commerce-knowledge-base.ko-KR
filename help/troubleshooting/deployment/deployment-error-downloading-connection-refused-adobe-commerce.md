---
title: '배포 오류: *다운로드 중 오류 7.. 포트 443: 연결이 거부되었습니다.*'
description: '이 문서에서는 배포 오류에 대한 솔루션을 제공합니다. *"다운로드 중 오류 7... 포트 443: 연결이 거부되었습니다."*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# 배포 오류: *다운로드 중 오류 7... 포트 443: 연결이 거부되었습니다*

이 문서에서는 다음 오류 메시지와 함께 배포에 실패하는 경우 발생하는 문제를 해결합니다.

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## 영향을 받는 버전

클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 문제

배포가 실패하고 **curl 오류 7** 메시지가 표시됩니다.

<u>재현 단계</u>:

배포를 트리거합니다.

<u>필요한 동작</u>:

배포가 완료되었습니다.

<u>실제 동작</u>:

배포가 실패하고 다음 오류가 발생했습니다. *curl 오류 7 다운로드하는 동안... 포트 443: 연결이 거부됨*&#x200B;이(가) 배포 로그에 나타납니다.

## 원인

이는 저장소에 대한 캐시 연결이 손실되기 때문일 수 있습니다.

## 솔루션

프로젝트의 수퍼 유저에게 이 명령 실행을 요청합니다.

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

프로젝트에서 누가 수퍼 유저인지 확인하려면 Commerce on Cloud Infrastructure Guide에서 [사용자의 프로젝트 역할 보기](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role)를 참조하십시오.

## 권장 읽기

* [Adobe Commerce 배포 문제 해결사](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html).
* [클라우드 저장소의 Adobe Commerce에 액세스할 수 없습니다. 배포 시 403 사용할 수 없음 또는 404 찾을 수 없음 오류](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [배포 실패. &quot;프로젝트 빌드 오류: 빌드 후크가 실패하고 상태 코드가 1&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
