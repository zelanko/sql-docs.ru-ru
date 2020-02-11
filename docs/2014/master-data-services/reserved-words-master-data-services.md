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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482574"
---
# <a name="reserved-words-master-data-services"></a>Зарезервированные слова (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]при создании элементов и объектов модели нельзя использовать некоторые слова. В противном случае могут возникнуть ошибки.  
  
> [!NOTE]  
>  Кроме того, следует ограничить использование специальных знаков (особых символов, знаков переноса и т. п.).  
  
-   [Модели](#models)  
  
-   [Сущности](#entities)  
  
-   [Явные иерархии](#exhierarchies)  
  
-   [Атрибуты](#attributes)  
  
-   [Члены](#members)  
  
##  <a name="models"></a>Моделью  
 Если вы создаете модель с именем **Name, не**выбирайте параметр **создать сущность с тем же именем, что и модель** , поскольку **имя** не может использоваться для имени сущности.  
  
##  <a name="entities"></a>Объектах  
 В качестве имен сущностей нельзя указывать **Name** и **Code**.  
  
##  <a name="exhierarchies"></a>Явные иерархии  
 В качестве имен явных иерархий нельзя указывать **Name** и **Code**.  
  
##  <a name="attributes"></a>Атрибута  
  
-   **УДОСТОВЕРЕНИЯ**  
  
-   **Код**  
  
-   **Название**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a>Участниками  
 Для элементов нельзя использовать **MDMMemberStatus** или **root** в качестве значения атрибута **Code** .  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о службах Master Data Services](master-data-services-overview-mds.md)  
  
  
