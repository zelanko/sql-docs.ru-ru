---
title: Что&#39;s нового (службы Integration Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6eda4eb4f01819bd569a472df01a276c5f270f31
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383107"
---
# <a name="what39s-new-integration-services"></a>Что&#39;s нового (службы Integration Services)
  В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] нет изменений по сравнению с предыдущим выпуском.  
  
 Дополнительные сведения о других [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] продуктов и технологий, см. в разделе [новые возможности в SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Дополнительные сведения об изменениях, связанных с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] бизнес-аналитики, см. в разделе [новые возможности служб Analysis Services и бизнес-аналитики](../analysis-services/what-s-new-in-analysis-services.md).  
  
##  <a name="ValidateXML"></a> Подробные данные о проверке XML в задачах XML  
 Активировав в задаче XML свойство `ValidationDetails`, вы сможете получить подробные результаты проверки XML-документа. До появления свойства `ValidationDetails` проверка XML в задачах XML возвращала информацию только о том, есть ошибка в документе или нет. Сведения о самих ошибках и их расположении были недоступны. Теперь, если для свойства `ValidationDetails` задать значение True, выходной файл будет содержать подробные сведения обо всех ошибках, включая номера строк и позиции. Эти сведения можно использовать для анализа, поиска и исправления ошибок в XML-документах. Дополнительные сведения см. в разделе [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 В [!INCLUDE[ssIS](../includes/ssis-md.md)] свойство `ValidationDetails` появилось с выходом пакета обновления 2 для [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. В то время о новом свойстве не было никакой информации. Свойство `ValidationDetails` доступно также в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] и SQL Server 2016.  
  
## <a name="see-also"></a>См. также  
 [Возможности, поддерживаемые различными выпусками SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
