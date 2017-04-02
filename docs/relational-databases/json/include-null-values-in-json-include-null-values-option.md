---
title: "Использование параметра INCLUDE_NULL_VALUES для включения значений Null в выходные данные JSON (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "INCLUDE_NULL_VALUES (для JSON)"
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 13
---
# Использование параметра INCLUDE_NULL_VALUES для включения значений Null в выходные данные JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Чтобы выходные данные JSON предложения **FOR JSON** содержали значения NULL, укажите параметр **INCLUDE_NULL_VALUES**.  
  
 Если параметр **INCLUDE_NULL_VALUES** не указан, в выходные данные JSON не будут включены те свойства, для которых в результатах запроса указаны значения NULL.  
  
## Примеры  
 В следующем примере показаны выходные данные предложения **FOR JSON** с параметром **INCLUDE_NULL_VALUES** и без него.  
  
|Без параметра **INCLUDE_NULL_VALUES**|С параметром **INCLUDE_NULL_VALUES**|  
|--------------------------------------------------|-----------------------------------------------|  
|`{    "name": "John",    "surname": "Doe" }`|`{    "name": "John",    "surname": "Doe",    "age": null,    "phone": null }`|  
  
 Вот другой пример предложения **FOR JSON** с параметром **INCLUDE_NULL_VALUES**.  
  
 **Запрос**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO, INCLUDE_NULL_VALUES  
```  
  
 **Результат**  
  
```json  
[   
   {"name": "John",  "surname": null },  
   {"name": "Jane",  "surname": "Doe"}  
]  
```  
  
## См. также:  
 [Предложение FOR (Transact-SQL)](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  