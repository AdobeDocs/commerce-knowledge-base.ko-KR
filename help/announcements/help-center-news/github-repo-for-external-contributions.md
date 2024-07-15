---
title: Adobe Commerce 지원 기술 자료에서 기여 접수를 시작합니다.
description: 6월 15일부터 Adobe Commerce 지원 기술 자료 팀은 [magento/knowledge-base](https://github.com/magento/knowledge-base) GitHub 리포지토리를 통해 외부 Adobe Commerce 커뮤니티에서 직접 편집 및 새 문서 기여 접수를 시작합니다.
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Adobe Commerce 지원 기술 자료에서 기여 접수를 시작합니다.

6월 15일부터 Adobe Commerce 지원 기술 자료 팀은 [magento/knowledge-base](https://github.com/magento/knowledge-base) GitHub 리포지토리를 통해 외부 Adobe Commerce 커뮤니티에서 직접 편집 내용 및 새 문서 기여 신청을 받습니다.

문서 중 하나에서 오타가 발생하거나 문제 해결 단계가 완료되지 않은 것을 발견했습니다.
이제 직접 수정하고 기여 점수를 받을 수 있습니다!

## Contribute

사소한 오타 수정부터 문제 해결 문서 완료까지 모든 종류의 기여를 환영합니다. 이 리포지토리에 기여하면 Adobe Commerce 코드 및 개발자 설명서에 기여하는 것과 유사한 보상 포인트를 얻을 수 있습니다. 자세한 내용은 [기여도 보상 포인트](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md)를 참조하세요.

### 일반 기여도 흐름

1. 이 리포지토리를 포크합니다.
1. 포크된 리포지토리를 편집합니다.
1. 이 저장소에 끌어오기 요청(PR)을 제출합니다.
1. 테스트 실행:
   * Adobe CLA - Adobe Open Source 기여자 라이선스 계약이 체결되었는지 확인합니다.
   * Markdown Linting 테스트 - Markdown 구문이 올바른지 확인합니다.
   * 파일 구조 유효성 검사 테스트 - [필요한 파일 구조](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure)에 따라 커밋이 수행되었는지 확인합니다.
1. PR 승인 흐름:
   1. 지원 기술 자료(KB) 작성자는 며칠 내에 PR을 검토하고 레이블을 추가합니다.
   1. KB 작성기는 변경 사항을 승인/거부/요청할 수 있습니다.
   1. 승인되면 KB라이터는 PR에서 제공된 입력 수준에 해당하는 라벨을 추가하고 내부주제전문가(SME)가 PR을 검토한다.
   1. SME가 변경을 승인/거부/요청할 수 있습니다.
1. 모든 수정이 완료되고(필요한 경우) KB 작성기와 SME가 모두 PR을 승인하면 KB 작성기는 콘텐츠를 내부 리포지토리로 가져와 내부적으로 병합합니다.
1. [magento/knowledge-base](https://github.com/magento/knowledge-base) 리포지토리가 20분 후에 내부 리포지토리와 동기화됩니다.
1. 보고서가 동기화되면 PR이 닫히고 [기여도 포인트](#contribution-points)가 제공됩니다.

기여 흐름에 대한 자세한 내용은 [기여자 안내서](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md)를 참조하세요.
서식 파일, 스타일 안내서 및 서식 지침은 [설명서](https://github.com/magento/knowledge-base/tree/main/docs)를 참조하세요.

### Github에서 지원 KB 문서 파일 찾기

지원 기술 자료(KB)에서 문서는 범주 아래에 중첩된 섹션으로 구성됩니다.

예를 들어 [Adobe Magento 상태 업데이트를 구독하는 방법](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md) 문서는 방법 범주의 일반 섹션에 속합니다.

문서 페이지의 탐색 표시 경로에서 섹션과 카테고리 이름을 볼 수 있습니다. 아래 이미지를 참조하십시오.

![범주 및 섹션 탐색 표시](assets/breadcrumbs.png)

문서 파일은 [magento/knowledge-base](https://github.com/magento/knowledge-base) 리포지토리에서 같은 방식으로 구성됩니다.
모든 콘텐츠는 `src` 폴더에 저장되며, 범주 폴더와 섹션 폴더가 중첩됩니다. 파일 이름은 문서 제목과 일치하거나 비슷합니다.

지원 KB 문서의 텍스트 일부를 검색 문자열로 사용하여 저장소 내에서 검색을 사용할 수도 있습니다. 검색에서 이 문자열을 포함하는 파일을 반환할 때 올바른 섹션 및 범주에 속하는 파일을 선택해야 합니다.

### 기여도 점수

기여도 점수 및 지원을 위해 Magento 커뮤니티 엔지니어링과 통합된 [magento/knowledge-base](https://github.com/magento/knowledge-base) 리포지토리입니다.

포인트가 어떻게 보상되는지 확인하려면 [기여도 포인트](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) 문서를 참조하십시오.
