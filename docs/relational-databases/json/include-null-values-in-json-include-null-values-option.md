---
title: "INCLUDE_NULL_VALUES для включения значений Null в JSON | Документация Майкрософт"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: INCLUDE_NULL_VALUES (FOR JSON)
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 70f50dc60738cc80379626d2a00d471e481906ea
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="include-null-values-in-json---includenullvalues-option"></a>INCLUDE_NULL_VALUES для включения значений Null в JSON
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Чтобы выходные данные JSON предложения **FOR JSON** содержали значения NULL, укажите параметр **INCLUDE_NULL_VALUES** .  
  
 Если параметр **INCLUDE_NULL_VALUES** не указан, в выходные данные JSON не будут включены те свойства, для которых в результатах запроса указаны значения NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показаны выходные данные предложения **FOR JSON** с параметром **INCLUDE_NULL_VALUES** и без него.  
  
|Без параметра **INCLUDE_NULL_VALUES**|С параметром **INCLUDE_NULL_VALUES**|  
|--------------------------------------------------|-----------------------------------------------|  
|`{    "name": "John",    "surname": "Doe" }`|`{    "name": "John",    "surname": "Doe",    "age": null,    "phone": null }`|  
  
 Вот другой пример предложения **FOR JSON** с параметром **INCLUDE_NULL_VALUES** .  
  
 **Запрос**  
  
```sql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO, INCLUDE_NULL_VALUES    
```  
  
 **Результат**  
  
```json  
[{
    "name": "John",
    "surname": null
}, {
    "name": "Jane",
    "surname": "Doe"
}] 
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Большое количество решений, варианты использования и рекомендации см. в [записях Йована Поповича (Jovan Popovic), руководителя программы Майкрософт, в блогах о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) в SQL Server и базах данных SQL Azure.  

## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  
