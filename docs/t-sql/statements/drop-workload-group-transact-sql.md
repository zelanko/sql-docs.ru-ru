---
title: DROP WORKLOAD GROUP (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP_WORKLOAD_GROUP_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD GROUP statement
ms.assetid: 1cd68450-5b58-4106-a2bc-54197ced8616
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 39815705fa0847c7e69d142ebd19486a0124a377
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="drop-workload-group-transact-sql"></a>DROP WORKLOAD GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет существующую, определяемую пользователем группу рабочей нагрузки регулятора ресурсов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP WORKLOAD GROUP group_name  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *group_name*  
 Имя существующей, определяемой пользователем группы рабочей нагрузки.  
  
## <a name="remarks"></a>Remarks  
 Использование инструкции DROP WORKLOAD GROUP не допускается для внутренней группы или группы по умолчанию регулятора ресурсов.  
  
 При выполнении инструкций DDL рекомендуется иметь представление о состояниях регулятора ресурсов. Дополнительные сведения см. в разделе [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) (Регулятор ресурсов).  
  
 Если группа рабочей нагрузки содержит активные сеансы, удаление или перемещение этой группы в другой пул ресурсов завершится неудачно при вызове инструкции ALTER RESOURCE GOVERNOR RECONFIGURE для применения изменения. Во избежание этой проблемы можно предпринять одно из следующих действий.  
  
-   Подождать, пока все сеансы затронутых групп завершатся, и заново выполнить инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
-   Явно остановить сеанс в затронутой группе, используя команду KILL, и затем заново выполнить инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
-   Перезапустите сервер. После завершения процесса перезапуска удаленная группа не будет создана, а перемещенная группа будет использовать новое назначение пула ресурсов.  
  
-   Если при выполнении сценария с инструкцией DROP WORKLOAD GROUP решено не останавливать сеанс явно для применения изменений, то можно создать заново группу, используя то же имя для нее, которое она имела до объявления оператора DROP, и потом переместить группу в исходный пул ресурсов. Чтобы применить изменения, выполните инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется группа рабочей нагрузки с именем `adhoc`.  
  
```  
DROP WORKLOAD GROUP adhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
