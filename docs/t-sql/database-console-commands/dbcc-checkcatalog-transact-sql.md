---
title: DBCC CHECKCATALOG (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC_CHECKCATALOG_TSQL
- DBCC CHECKCATALOG
- CHECKCATALOG_TSQL
- CHECKCATALOG
dev_langs:
- TSQL
helpviewer_keywords:
- catalogs [SQL Server], consistency checks
- checking catalog consistency
- DBCC CHECKCATALOG statement
- integrity [SQL Server], catalogs
- consistency [SQL Server], catalogs
ms.assetid: 8076eb4e-f049-44bf-9a35-45cdd6ef0105
author: pmasl
ms.author: umajay
ms.openlocfilehash: d75739e2a8594bbd049a7d9b1c2a6908b1c0e29c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68102201"
---
# <a name="dbcc-checkcatalog-transact-sql"></a>DBCC CHECKCATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Проверяет согласованность каталогов в указанной базе данных. База данных должна быть в режиме в сети.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DBCC CHECKCATALOG   
[   
    (   
    database_name | database_id | 0  
    )  
]  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name* | *database_id* | 0  
 Название или идентификатор базы данных, для которой проверяется согласованность каталогов. Если значение не указано или указано значение 0, используется текущая база данных. Имена баз данных должны соответствовать правилам [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
 WITH NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Remarks  
После выполнения команды DBCC CATALOG в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывается сообщение. При успешном выполнении команды DBCC сообщается об успешном завершении и количестве времени, затраченном на выполнение команды. Если выполнение команды DBCC прерывается до завершения проверки по причине ошибки, сообщение указывает на прерывание команды и приводит значение состояния и количество времени, затраченного на выполнение команды. В следующей таблице перечислены и описаны значения состояний, которые могут быть включены в сообщение.
  
|Штат|Description|  
|-----------|-----------------|  
|0|Возникла ошибка с номером 8930. Это указывает на повреждение метаданных, вызвавшее прекращение выполнения команды DBCC.|  
|1|Возникла ошибка с номером 8967. Внутренняя ошибка DBCC.|  
|2|При аварийном восстановлении базы данных произошла ошибка.|  
|3|Это указывает на повреждение метаданных, вызвавшее прекращение выполнения команды DBCC.|  
|4|Обнаружено нарушение доступа или утверждения.|  
|5|Возникла неизвестная ошибка, которая привела к прекращению выполнения команды DBCC.|  
  
DBCC CHECKCATALOG выполняет различные проверки подлинности между системными таблицами метаданных. DBCC CHECKCATALOG использует моментальный снимок внутренней базы данных для предоставления согласованности транзакций, которые ему необходимы для выполнения этих проверок. Дополнительные сведения см. в статье [Просмотр размера разреженного файла снимка базы данных (Transact-SQL)](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md) и разделе "Использование внутреннего моментального снимка базы данных в командах DBCC" статьи [DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md).
Если моментальный снимок базы данных не может быть создан, DBCC CHECKCATALOG применяет монопольную блокировку базы данных для обеспечения необходимой согласованности. Если обнаружены несогласованности, они не подлежат исправлению и база данных должна быть восстановлена из резервной копии.
  
> [!NOTE]  
> При выполнении инструкции DBCC CHECKCATALOG для базы данных **tempdb** никакие проверки не выполняются. Это обусловлено тем, что по соображениям производительности моментальные снимки базы данных недоступны для базы данных **tempdb**. Это означает, что нельзя достичь требуемой согласованности транзакций. Перезапустите сервер для решения любых проблем с метаданными **tempdb**.  
  
> [!NOTE]  
> Инструкция DBCC CHECKCATALOG не проверяет данные FILESTREAM. FILESTREAM сохраняет в файловой системе большие двоичные объекты.  
  
DBCC CHECKCATALOG также выполняется как часть при выполнении [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).
  
## <a name="result-sets"></a>Результирующие наборы  
Если не указана база данных, DBCC CHECKCATALOG возвращает:
  
```
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
Если в качестве базы данных указано [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], DBCC CHECKCATALOG возвращает:
  
```
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner**.  
  
## <a name="examples"></a>Примеры  
Следующий пример проверяет целостность каталогов в текущей базе данных и в базе данных `AdventureWorks`.
  
```sql
-- Check the current database.  
DBCC CHECKCATALOG;  
GO  
-- Check the AdventureWorks2012 database.  
DBCC CHECKCATALOG (AdventureWorks2012);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)
  
