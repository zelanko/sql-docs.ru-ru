---
title: "Пример набора записей для изучения данных | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
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
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c03e0c912234a73bc62a5b4916367a2583a9c71c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
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
