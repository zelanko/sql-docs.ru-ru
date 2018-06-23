---
title: Зарезервированные слова (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3307fb8185abfb6b862e72691596e4385b09dcb8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194518"
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
  
##  <a name="models"></a> Модели  
 Если создать модель с именем, заданным **имя**, не устанавливайте **создать сущность с именем модели** из-за **имя** не может использоваться в качестве имени сущности.  
  
##  <a name="entities"></a> Сущности  
 В качестве имен сущностей нельзя указывать **Name** и **Code**.  
  
##  <a name="exhierarchies"></a> Явные иерархии  
 В качестве имен явных иерархий нельзя указывать **Name** и **Code**.  
  
##  <a name="attributes"></a> Атрибуты  
  
-   **Идентификатор**  
  
-   **Code**  
  
-   **Название**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> Члены  
 Для элементов, не может использовать **MDMMemberStatus** или **КОРНЕВОЙ** для **код** значение атрибута.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о службах Master Data Services](master-data-services-overview-mds.md)  
  
  