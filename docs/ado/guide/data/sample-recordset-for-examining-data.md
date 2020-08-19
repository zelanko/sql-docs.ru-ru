---
description: Пример набора записей для проверки данных
title: Пример набора записей для проверки данных | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f4c989667d5b4a5ceb3fb0c4f4d929e49be92e00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452916"
---
# <a name="sample-recordset-for-examining-data"></a>Пример набора записей для проверки данных
Сначала рассмотрим объект **Recordset** , возвращенный с помощью следующего запроса SQL, выполненного для базы данных "Northwind Sample Data" в Microsoft SQL Server.  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 Результирующий объект **набора записей** содержит все объекты, которые создает в базе данных, показанной в следующей таблице.  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|Дядюшканые груши Высохнутьы Боба|30,0000|  
|14|тофу|23,2500|  
|28|Рссле квашеной|45,6000|  
|51|Манжимуп высохнуть яблоки|53,0000|  
|74|Лонглифе тофу|10,0000|  
  
 Если вы хотите получить эти результаты самостоятельно, попробуйте следующий пример в JScript:  
  
-   [Пример JScript для возврата набора записей](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
