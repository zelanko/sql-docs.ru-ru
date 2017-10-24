---
title: "Инструкция DBCC TRACESTATUS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC_TRACESTATUS_TSQL
- DBCC TRACESTATUS
- TRACESTATUS_TSQL
- TRACESTATUS
dev_langs:
- TSQL
helpviewer_keywords:
- global trace flags [SQL Server]
- status information [SQL Server], trace flags
- trace flags [SQL Server], status information
- DBCC TRACESTATUS statement
- session trace flags [SQL Server]
- displaying trace flag status
ms.assetid: 9be51199-78b4-4b87-ae6e-557246b7e29a
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 75d78069427891cfab6f7aaef7192d498912611a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-tracestatus-transact-sql"></a>DBCC TRACESTATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Отображает состояние флагов трассировки.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC TRACESTATUS ( [ [ trace# [ ,...n ] ] [ , ] [ -1 ] ] )   
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
*Trace #*  
Номер флага трассировки, для которого отображается состояние. Если *trace #*и -1 не указаны, то отображаются все флаги трассировки, которые включены для сеанса.
  
*n*  
Заполнитель, показывающий, что можно задавать несколько флагов трассировки.
  
-1  
Отображает состояние глобально активированных флагов трассировки. Если задано значение -1, без *trace #*, отображаются все глобальные флаги трассировки, включены.
  
WITH NO_INFOMSGS  
Подавляет все информационные сообщения со степенями серьезности от 0 до 10.
  
## <a name="result-sets"></a>Результирующие наборы  
В следующей таблице описаны сведения в результирующем наборе.
  
|Имя столбца|Description|  
|---|---|
|**TraceFlag**|Имя флага трассировки.|  
|**Состояние**|Показывает, как задан глобальный или сеансовый флаг трассировки (включен или выключен):<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|**Глобальные**|Показывает, задан ли флаг трассировки глобально;<br /><br /> 1 = True<br /><br /> 0 = False.|  
|**Сеанс**|Показывает, задан ли флаг трассировки для сеанса:<br /><br /> 1 = True<br /><br /> 0 = False.|  
  
Инструкция DBCC TRACESTATUS возвращает столбец с номерами флагов трассировки и столбец их состояний. Показывает, включен (1) или выключен (2) флаг трассировки. Столбец заголовков для номеров флагов трассировки может либо **глобальный флаг трассировки** или **Session Trace Flag**, в зависимости от, отражающие состояние глобально или флага трассировки.
  
## <a name="remarks"></a>Замечания  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] существуют два типа флагов трассировки: для сеанса и глобальные. Флаги трассировки сеанса действуют во время данного соединения и доступны только для этого соединения. Глобальные флаги трассировки устанавливаются на уровне сервера и доступны для каждого соединения с этим сервером.
  
## <a name="permissions"></a>Permissions  
Необходимо быть членом роли **public** .
  
## <a name="examples"></a>Примеры  
В следующем примере отображается состояние глобально активированных флагов трассировки.
  
```sql  
DBCC TRACESTATUS(-1);  
GO  
```  
  
В следующем примере отображается состояние флагов трассировки `2528` и `3205`.
  
```sql  
DBCC TRACESTATUS (2528, 3205);  
GO  
```  
  
В следующем примере выясняется, активирован ли флаг трассировки `3205` глобально.
  
```sql  
DBCC TRACESTATUS (3205, -1);  
GO  
```  
  
В ходе выполнения следующего примера отображается список всех флагов трассировки, активированных для данного сеанса.
  
```sql  
DBCC TRACESTATUS();  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC TRACEOFF (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceoff-transact-sql.md)  
[DBCC TRACEON (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md)  
[Флаги трассировки (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  

