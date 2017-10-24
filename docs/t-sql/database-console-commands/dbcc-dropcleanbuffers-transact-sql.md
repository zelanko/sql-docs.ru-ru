---
title: "DBCC DROPCLEANBUFFERS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROPCLEANBUFFERS
- DBCC_DROPCLEANBUFFERS_TSQL
- DROPCLEANBUFFERS_TSQL
- DBCC DROPCLEANBUFFERS
dev_langs:
- TSQL
helpviewer_keywords:
- clean buffers
- cold buffer cache
- buffer pools [SQL Server]
- dropping buffers
- removing buffers
- DBCC DROPCLEANBUFFERS statement
ms.assetid: a4121927-f2ce-4926-aa2c-9b1519dac048
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d1a7a1507e230995df1c2b67a8499a12270b535c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-dropcleanbuffers-transact-sql"></a>DBCC DROPCLEANBUFFERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

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
  
## <a name="remarks"></a>Замечания  
С помощью инструкции DBCC DROPCLEANBUFFERS можно выполнить проверку запроса при холодном буферном кэше, не выключая и не перезапуская сервер.
Чтобы удалить чистые буферы из буферного пула и columnstore объектов из объектном пуле, сначала воспользоваться инструкцией CHECKPOINT для создания холодного буферного кэша. Это вызовет принудительную запись всех «грязных» страниц текущей базы данных на диск и очистит буферы. После этого можно выполнить команду DBCC DROPCLEANBUFFERS, которая удалит все буферы из буферного пула.
  
## <a name="result-sets"></a>Результирующие наборы  
DBCC DROPCLEANBUFFERS на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  

Применяется к: SQL Server, параллельные хранилища данных 

- Необходимо членство в предопределенной роли сервера **sysadmin** .  

Область применения этой статьи: Хранилище данных SQL Azure

- Требуется членство в фиксированной серверной роли DB_OWNER.  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[CHECKPOINT (Transact-SQL)](../../t-sql/language-elements/checkpoint-transact-sql.md)  
  
  

