---
title: Зарезервированные слова (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 5435c2a48417156abd6d4f831bf61c9ba6440fab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65482574"
---
# <a name="reserved-words-master-data-services"></a>Зарезервированные слова (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]при создании элементов и объектов модели нельзя использовать некоторые слова. В противном случае могут возникнуть ошибки.  
  
> [!NOTE]  
>  Кроме того, следует ограничить использование специальных знаков (особых символов, знаков переноса и т. п.).  
  
-   [Модели](#models)  
  
-   [Entities](#entities)  
  
-   [Явные иерархии](#exhierarchies)  
  
-   [Атрибуты](#attributes)  
  
-   [Участниками](#members)  
  
##  <a name="models"></a><a name="models"></a>Моделью  
 Если вы создаете модель с именем **Name, не**выбирайте параметр **создать сущность с тем же именем, что и модель** , поскольку **имя** не может использоваться для имени сущности.  
  
##  <a name="entities"></a><a name="entities"></a>Объектах  
 В качестве имен сущностей нельзя указывать **Name** и **Code**.  
  
##  <a name="explicit-hierarchies"></a><a name="exhierarchies"></a>Явные иерархии  
 В качестве имен явных иерархий нельзя указывать **Name** и **Code**.  
  
##  <a name="attributes"></a><a name="attributes"></a>Атрибута  
  
-   **Идентификатор**  
  
-   **Приведен**  
  
-   **Имя**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a><a name="members"></a>Участниками  
 Для элементов нельзя использовать **MDMMemberStatus** или **root** в качестве значения атрибута **Code** .  
  
## <a name="see-also"></a>См. также  
 [Обзор Master Data Services](master-data-services-overview-mds.md)  
  
  
