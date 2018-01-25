---
title: "DBCC DROPCLEANBUFFERS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROPCLEANBUFFERS
- DBCC_DROPCLEANBUFFERS_TSQL
- DROPCLEANBUFFERS_TSQL
- DBCC DROPCLEANBUFFERS
dev_langs: TSQL
helpviewer_keywords:
- clean buffers
- cold buffer cache
- buffer pools [SQL Server]
- dropping buffers
- removing buffers
- DBCC DROPCLEANBUFFERS statement
ms.assetid: a4121927-f2ce-4926-aa2c-9b1519dac048
caps.latest.revision: "35"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aa4214f9bd043e31adb3f3e62340cbc023c9172d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-dropcleanbuffers-transact-sql"></a>DBCC DROPCLEANBUFFERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Удаляет все чистые буферы из буферного пула и columnstore объекты объектном пуле.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис
Синтаксис для SQL Server: 

```sql
DBCC DROPCLEANBUFFERS [ WITH NO_INFOMSGS ]  
```  
Синтаксис для хранилища Azure SQL и параллельные хранилища данных:

```sql  
DBCC DROPCLEANBUFFERS ( COMPUTE | ALL ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
 WITH NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений. Информационные сообщения всегда подавляются на [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 COMPUTE  
 Очистка кэша планов запросов из каждого вычислительного узла.  
  
 ALL  
 Очистка кэша планов запросов из каждый вычислительный узел и узел элемента управления. Это значение по умолчанию, если значение не указано.  
  
## <a name="remarks"></a>Remarks  
С помощью инструкции DBCC DROPCLEANBUFFERS можно выполнить проверку запроса при холодном буферном кэше, не выключая и не перезапуская сервер.
Чтобы удалить чистые буферы из буферного пула и columnstore объектов из объектном пуле, сначала воспользоваться инструкцией CHECKPOINT для создания холодного буферного кэша. Это вызовет принудительную запись всех «грязных» страниц текущей базы данных на диск и очистит буферы. После этого можно выполнить команду DBCC DROPCLEANBUFFERS, которая удалит все буферы из буферного пула.
  
## <a name="result-sets"></a>Результирующие наборы  
DBCC DROPCLEANBUFFERS на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  

Применяется к: SQL Server, параллельные хранилища данных 

- Необходимо членство в предопределенной роли сервера **sysadmin** .  

Область применения этой статьи: Хранилище данных SQL Azure

- Требуется членство в фиксированной серверной роли DB_OWNER.  
  
## <a name="see-also"></a>См. также  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[CHECKPOINT (Transact-SQL)](../../t-sql/language-elements/checkpoint-transact-sql.md)  
  
  
