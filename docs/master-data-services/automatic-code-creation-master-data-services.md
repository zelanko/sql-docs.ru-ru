---
title: Автоматическое создание кодов (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 24965436108df067d7bd4ea10b4ad1e71b9ce69e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727282"
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
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Автоматическое формирование значений для атрибута Code.|[Автоматическое формирование значений атрибута Code (службы Master Data Services)](../master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|Автоматическое формирование значений для других атрибутов.|[Автоматическое формирование значений атрибута, отличного от Code (службы Master Data Services)](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Общие сведения о службах Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
-   [Сущности (службы Master Data Services)](../master-data-services/entities-master-data-services.md)  
  
  
