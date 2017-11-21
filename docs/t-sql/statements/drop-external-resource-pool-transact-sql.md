---
title: "Удалить внешний ПУЛ РЕСУРСОВ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL RESOURCE POOL
- DROP_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL RESOURCE POOL statement
ms.assetid: e2fa01bd-96ff-4ea9-bb08-6cb6b6adf68c
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a0aae6de75280fb0e32879ece5acea6d0fd94f3c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-external-resource-pool-transact-sql"></a>Удалить внешний ПУЛ РЕСУРСОВ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Удаление пула внешних ресурсов регулятора ресурсов используются, чтобы определить ресурсы для внешних процессов. Для служб R управляет внешний пул `rterm.exe`, `BxlServer.exe`и порожденных ими процессов. Внешних пулов ресурсов, созданных с помощью [CREATE EXTERNAL RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-resource-pool-transact-sql.md) и изменяются с помощью [ALTER EXTERNAL RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-external-resource-pool-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP EXTERNAL RESOURCE POOL pool_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *pool_name*  
 Имя удаляемого пула внешних ресурсов.  
  
## <a name="remarks"></a>Замечания  
 Внешний пул ресурсов нельзя удалить, если он содержит группы рабочей нагрузки.  
  
 Нельзя удалить внутренний пул или пул по умолчанию регулятора ресурсов.  
  
 Перенастройка n  
  
 При выполнении инструкций DDL рекомендуется иметь представление о состояниях регулятора ресурсов. Дополнительные сведения см. в разделе [регулятора ресурсов](../../relational-databases/resource-governor/resource-governor.md).  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение `CONTROL SERVER`  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется внешний пул ресурсов с именем `ex_pool`.  
  
```  
DROP EXTERNAL RESOURCE POOL ex_pool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Параметр конфигурации сервера External scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [Службы R SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Известные проблемы для SQL Server R Services](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ИЗМЕНИТЬ внешний ПУЛ РЕСУРСОВ &#40; Transact-SQL &#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [DROP WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [УДАЛИТЬ ПУЛ РЕСУРСОВ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)  
  
  

