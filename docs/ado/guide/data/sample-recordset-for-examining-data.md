---
description: Пример набора записей для проверки данных
title: Пример набора записей для проверки данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: ec44c25bba9c792415c462e3028bbf20d8d3f84e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979745"
---
# <a name="sample-recordset-for-examining-data"></a>Пример набора записей для проверки данных
Сначала рассмотрим объект **Recordset** , возвращенный с помощью следующего запроса SQL, выполненного для базы данных "Northwind Sample Data" в Microsoft SQL Server.  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 Результирующий объект **набора записей** содержит все объекты, которые создает в базе данных, показанной в следующей таблице.  
  
|ProductID|ProductName|Цена за единицу|  
|---------------|-----------------|---------------|  
|7|Дядюшканые груши Высохнутьы Боба|30,0000|  
|14|тофу|23,2500|  
|28|Рссле квашеной|45,6000|  
|51|Манжимуп высохнуть яблоки|53,0000|  
|74|Лонглифе тофу|10,0000|  
  
 Если вы хотите получить эти результаты самостоятельно, попробуйте следующий пример в JScript:  
  
-   [Пример JScript для возврата набора записей](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
