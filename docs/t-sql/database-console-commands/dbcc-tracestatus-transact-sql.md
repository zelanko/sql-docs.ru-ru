---
description: DBCC TRACESTATUS (Transact-SQL)
title: DBCC TRACESTATUS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: pmasl
ms.author: umajay
ms.openlocfilehash: 046c8fa60fc4bc4930089d8c7e9a87a3480bff23
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417600"
---
# <a name="dbcc-tracestatus-transact-sql"></a>DBCC TRACESTATUS (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

Отображает состояние флагов трассировки.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DBCC TRACESTATUS ( [ [ trace# [ ,...n ] ] [ , ] [ -1 ] ] )   
[ WITH NO_INFOMSGS ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
*trace#*  
Номер флага трассировки, для которого отображается состояние. Если с аргументом *trace#* не задано значение –1, то отображаются все флаги трассировки данного сеанса.
  
*n*  
Заполнитель, показывающий, что можно задавать несколько флагов трассировки.
  
-1  
Отображает состояние глобально активированных флагов трассировки. Если значение –1 задано без аргумента *trace#*, то отображаются все активированные глобальные флаги трассировки.
  
WITH NO_INFOMSGS  
Подавляет все информационные сообщения со степенями серьезности от 0 до 10.
  
## <a name="result-sets"></a>Результирующие наборы  
В следующей таблице описаны сведения в результирующем наборе.
  
|Имя столбца|Описание|  
|---|---|
|**TraceFlag**|Имя флага трассировки.|  
|**Состояние**|Показывает, как задан глобальный или сеансовый флаг трассировки (включен или выключен):<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|**Глобальный**|Показывает, задан ли флаг трассировки глобально;<br /><br /> 1 = истина<br /><br /> 0 = ложь|  
|**Согласованность сеанса**|Показывает, задан ли флаг трассировки для сеанса:<br /><br /> 1 = истина<br /><br /> 0 = ложь|  
  
Инструкция DBCC TRACESTATUS возвращает столбец с номерами флагов трассировки и столбец их состояний. Показывает, включен (1) или выключен (2) флаг трассировки. Столбец заголовков для номеров флагов трассировки может содержать значения **Global Trace Flag** или **Session Trace Flag**, отражающие соответствующее состояние каждого флага трассировки.
  
## <a name="remarks"></a>Примечания  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] существуют два типа флагов трассировки: для сеанса и глобальные. Флаги трассировки сеанса действуют во время данного соединения и доступны только для этого соединения. Глобальные флаги трассировки устанавливаются на уровне сервера и доступны для каждого соединения с этим сервером.
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом роли **public**.
  
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
  
  
