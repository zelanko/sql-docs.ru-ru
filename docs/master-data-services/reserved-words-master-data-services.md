---
title: Зарезервированные слова
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 78dcf9320312f93dd08495f21bf0f6cc1b71516b
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811469"
---
# <a name="reserved-words-master-data-services"></a>Зарезервированные слова (службы Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]при создании элементов и объектов модели нельзя использовать некоторые слова. В противном случае могут возникнуть ошибки.  
  
> [!NOTE]  
>  Кроме того, следует ограничить использование специальных знаков (особых символов, знаков переноса и т. п.).  
  
-   [Модели](../master-data-services/reserved-words-master-data-services.md#models)  
  
-   [Сущности](../master-data-services/reserved-words-master-data-services.md#entities)  
  
-   [Явные иерархии](../master-data-services/reserved-words-master-data-services.md#exhierarchies)  
  
-   [Атрибуты](../master-data-services/reserved-words-master-data-services.md#attributes)  
  
-   [Члены](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a><a name="models"></a>Моделью  
 Если модель создается с именем **Name** или **Code**, не выбирайте **Создать сущность с именем модели** , поскольку **Name** или **Code** нельзя использовать в качестве имени сущности.  
  
##  <a name="entities"></a><a name="entities"></a>Объектах  
 В качестве имен сущностей нельзя указывать **Name** и **Code**.  
  
##  <a name="explicit-hierarchies"></a><a name="exhierarchies"></a>Явные иерархии  
 В качестве имен явных иерархий нельзя указывать **Name** и **Code**.  
  
##  <a name="attributes"></a><a name="attributes"></a>Атрибута  
  
-   **ID**  
  
-   **Код**  
  
-   **EnterUserName**  
  
-   **LastChgUserName**  
  
-   **Name**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a><a name="members"></a>Участниками  
 Для элементов нельзя использовать **MDMMemberStatus**, **MDMUnused**или **ROOT** в качестве значения атрибута **Code** .  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о службах Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
  
