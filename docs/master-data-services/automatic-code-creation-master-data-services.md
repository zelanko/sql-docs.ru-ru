---
title: Автоматическое создание кодов (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 82b145eb8a947c9320b4c4cb261d3a83e623d094
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="automatic-code-creation-master-data-services"></a>Автоматическое создание кодов (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]числовые значения могут автоматически формироваться для атрибута Code или другого числового атрибута. При автоматическом формировании кодов есть возможность ввода других значений для кодов вместо исходных, автоматически установленных значений.  
  
## <a name="generating-code-values"></a>Формирование значений кодов  
 Администратор может настроить автоматическое формирование значений для атрибута Code, изменив свойства связанных сущностей. Он может задать исходное значение и предусмотреть увеличение каждого последующего значения на единицу.  
  
 Когда значения атрибута Code вводятся в MDS — либо в одном из программных средств, либо с помощью промежуточного процесса, можно оставить этот атрибут пустым, и тогда значения будут сформированы автоматически. Также можно указать нужное вам значение Code.  
  
## <a name="generating-other-attribute-values"></a>Формирование других значений атрибутов  
 Администратор может автоматически сформировать значения для атрибутов, отличных от Code, создав бизнес-правила. Он может задать исходное значение и определить, насколько будут увеличиваться все последующие значения.  
  
 Когда значения атрибутов вводятся в MDS — либо с помощью одного из программных средств, либо с помощью промежуточного процесса — можно оставить значение атрибута пустым. При использовании бизнес-правил значения будут наращиваться, исходя из наибольшего существующего значения. Например, если правило звучит как «Задать для атрибута формируемое значение по умолчанию начиная с 1, с увеличением последующих значений на 4» и наибольшее значение атрибута равно 700, то следующий добавленный элемент будет равняться 704.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Автоматическое формирование значений для атрибута Code.|[Автоматическое формирование значений атрибута Code (службы Master Data Services)](../master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|Автоматическое формирование значений для других атрибутов.|[Автоматическое формирование значений атрибута, отличного от Code (службы Master Data Services)](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Общие сведения о службах Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
-   [Сущности (службы Master Data Services)](../master-data-services/entities-master-data-services.md)  
  
  
