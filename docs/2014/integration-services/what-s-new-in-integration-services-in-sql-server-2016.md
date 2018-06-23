---
title: Что&#39;s нового (службы Integration Services) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
caps.latest.revision: 112
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c7d37fb3c1d2cd1dcafecc012fbe83e1864e50ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094804"
---
# <a name="what39s-new-integration-services"></a>Что&#39;s нового (службы Integration Services)
  В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] нет изменений по сравнению с предыдущим выпуском.  
  
 Дополнительные сведения о других [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] продуктов и технологий, в разделе [новые возможности SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Дополнительные сведения об изменениях, связанных с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] бизнес-аналитики, в разделе [новые возможности служб Analysis Services и бизнес-аналитики](../analysis-services/what-s-new-in-analysis-services.md).  
  
##  <a name="ValidateXML"></a> Подробные данные о проверке XML в задачах XML  
 Проверка XML-документов и получить подробные результаты, включив `ValidationDetails` свойства задачи «XML». Прежде чем `ValidationDetails` было предусмотрено, проверка XML в задачах XML возвращаются только true или false, без информации об ошибках и их расположении. Теперь, если для свойства `ValidationDetails` значение true, выходной файл содержит подробные сведения обо всех ошибках, включая номер строки и позиции. Эти сведения можно использовать для анализа, поиска и исправления ошибок в XML-документах. Дополнительные сведения см. в разделе [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] представленные `ValidationDetails` свойство в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] с пакетом обновления 2. В то время о новом свойстве не было никакой информации. `ValidationDetails` Также это свойство доступно в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] и в SQL Server 2016.  
  
## <a name="see-also"></a>См. также  
 [Возможности, поддерживаемые различными выпусками SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  