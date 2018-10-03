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
manager: craigg
ms.openlocfilehash: bfae67a14fb312f1b396cfc60f69e8cbe8babdf7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811442"
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
