---
title: Что&#39;s нового (службы Integration Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7427402df49625c04ab7d1c38dd6bcfe3298e0ed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048544"
---
# <a name="what39s-new-integration-services"></a>Что&#39;s нового (службы Integration Services)
  В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] нет изменений по сравнению с предыдущим выпуском.  
  
 Дополнительные сведения о других [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] продуктов и технологий, см. в разделе [новые возможности в SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Дополнительные сведения об изменениях, связанных с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] бизнес-аналитики, см. в разделе [новые возможности служб Analysis Services и бизнес-аналитики](../analysis-services/what-s-new-in-analysis-services.md).  
  
##  <a name="ValidateXML"></a> Подробные данные о проверке XML в задачах XML  
 Проверка XML-документов и настроить вывод подробных сведений об ошибках, включив `ValidationDetails` свойства задачи «XML». Прежде чем `ValidationDetails` был предусмотрен, проверка XML в задачах XML возвращаются только true или false, без сведений об ошибках и их расположении. Теперь, если для свойства `ValidationDetails` в значение true, выходной файл содержит подробные сведения обо всех ошибках, включая номер строки и позиции. Эти сведения можно использовать для анализа, поиска и исправления ошибок в XML-документах. Дополнительные сведения см. в разделе [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] представленные `ValidationDetails` свойство в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] с пакетом обновления 2. В то время о новом свойстве не было никакой информации. `ValidationDetails` Свойство также доступно в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] и в SQL Server 2016.  
  
## <a name="see-also"></a>См. также  
 [Возможности, поддерживаемые различными выпусками SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
