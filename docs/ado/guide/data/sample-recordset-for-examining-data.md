---
title: "Пример набора записей для изучения данных | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: edc5419a18d658d9a0e10dc40b69ceb41c730bd4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sample-recordset-for-examining-data"></a>Образец набора записей для анализа данных
Во-первых давайте взглянем на **записей** объектом, возвращаемым при помощи следующего запроса SQL, выполняется на основе образцов данных Northwind, базовый в Microsoft SQL Server.  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 Итоговые **записей** объект содержит все создает в базе данных, показанные в следующей таблице.  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|Боб родственным органических высохла Груши|30.0000|  
|14|Диаграмме|23.2500|  
|28|Квашеная капуста Rssle|45.6000|  
|51|Сушеные яблоки|53.0000|  
|74|Longlife диаграмме|10.0000|  
  
 Если вы заинтересованы в получении эти результаты самостоятельно, попробуйте использовать в следующем примере JScript.  
  
-   [Пример JScript для возвращения набора записей](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)

