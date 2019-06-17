---
title: Пример набора записей для изучения данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9ffc34dd95ac2f5ef6e26e796c4c05cd91b28ae0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700397"
---
# <a name="sample-recordset-for-examining-data"></a>Пример набора записей для проверки данных
Во-первых давайте взглянем на **записей** как возвращаются с помощью следующий запрос SQL, выполняется на основе демонстрационных данных "Борей", в Microsoft SQL Server.  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 Полученный **записей** объект содержит то дает результат в базе данных, показано в следующей таблице.  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|Uncle Bob органических высохла Груши|30.0000|  
|14|Диаграмме|23.2500|  
|28|Квашеной Rssle|45.6000|  
|51|Сушеные яблоки|53.0000|  
|74|Longlife диаграмме|10.0000|  
  
 Если вы заинтересованы в получении этих результатов, самостоятельно, попробуйте в следующем примере JScript:  
  
-   [Пример JScript, возвращающего набор записей](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
