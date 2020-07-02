---
title: sp_attach_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_attach_db_TSQL
- sp_attach_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_db
ms.assetid: 59bc993e-7913-4091-89cb-d2871cffda95
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f42ab54f6e571e0cafa0498f852bbe52d3b43ef8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716207"
---
# <a name="sp_attach_db-transact-sql"></a>sp_attach_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Присоединение базы данных к серверу.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого рекомендуется использовать CREATE DATABASE *database_name* для Attach. Дополнительные сведения см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
> [!NOTE]  
>  Для перестроения нескольких файлов журнала, если одно или несколько из них имеют новое расположение, используйте CREATE DATABASE *database_name* для ATTACH_REBUILD_LOG.  
  
> [!IMPORTANT]  
>  Не рекомендуется подключать или восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_attach_db [ @dbname= ] 'dbname'  
    , [ @filename1= ] 'filename_n' [ ,...16 ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'dbnam_ '`Имя базы данных, которая будет присоединена к серверу. Имя должно быть уникальным. Аргумент *dbname* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @filename1 = ] 'filename_n'`Физическое имя файла базы данных, включая путь. *filename_n* имеет тип **nvarchar (260)** и значение по умолчанию NULL. Можно указать до 16 имен файлов. Имена параметров начинаются с ** \@ имя_файла1** и увеличиваются в ** \@ filename16**. Список имен файлов должен включать хотя бы первичный файл. Первичный файл содержит системные таблицы, указывающие на другие файлы базы данных. Список также должен включать все файлы, перемещенные после отключения базы данных.  
  
> [!NOTE]  
>  Этот аргумент сопоставляется с параметром FILENAME инструкции CREATE DATABASE. Дополнительные сведения см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
>   
>  Когда базу данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с файлами полнотекстовых каталогов присоединяют к экземпляру сервера [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , то присоединение файлов каталогов выполняется из их предыдущего расположения вместе с другими файлами баз данных, как и в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения см. в разделе [Обновление полнотекстового поиска](../../relational-databases/search/upgrade-full-text-search.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Хранимая процедура **sp_attach_db** должна выполняться только для баз данных, которые ранее были отключены от сервера базы данных с помощью явной операции **sp_detach_db** или для скопированных баз данных. Если необходимо указать более 16 файлов, используйте *DATABASE_NAME* создания базы данных для присоединения или создания базы данных *database_name* FOR_ATTACH_REBUILD_LOG. Дополнительные сведения см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
 Предполагается, что любые неуказанные файлы находятся в своем последнем известном расположении. Чтобы использовать файл, расположенный в другом месте, необходимо указать его новое расположение.  
  
 База данных, созданная в более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не может быть присоединена в ранних версиях.  
  
> [!NOTE]  
>  Невозможно отсоединить или присоединить моментальный снимок базы данных.  
  
 При подключении реплицируемой базы данных, которая была скопирована, а не отсоединена, необходимо учитывать следующее.  
  
-   При подключении базы данных к тому же экземпляру и версии сервера, к которому была подключена оригинальная база данных, не требуется никаких дополнительных действий.  
  
-   При подключении базы данных к обновленной версии того же экземпляра сервера необходимо запустить процедуру [sp_vupgrade_replication](../../relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql.md) для обновления репликации по завершении операции подключения.  
  
-   При подключении базы данных к другому экземпляру сервера, независимо от его версии, необходимо запустить процедуру [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) для удаления репликации по завершении операции подключения.  
  
 При первом присоединении базы данных к новому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или ее восстановлении копия главного ключа базы данных (зашифрованная главным ключом службы) еще не хранится на сервере. Необходимо расшифровать главный ключ базы данных с помощью инструкции **OPEN MASTER KEY**. Как только главный ключ базы данных будет расшифрован, появится возможность разрешить автоматическую расшифровку в будущем с помощью инструкции **ALTER MASTER KEY REGENERATE**, чтобы оставить на сервере копию главного ключа базы данных, зашифрованного с помощью главного ключа службы. После обновления базы данных с переходом от более ранней версии главный ключ базы данных должен быть создан повторно для использования нового алгоритма шифрования AES. Дополнительные сведения о повторном создании главного ключа базы данных см. в статье [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md). Время, необходимое для повторного создания главного ключа базы данных с обновлением до алгоритма шифрования AES, зависит от числа объектов, защищаемых главным ключом базы данных. Повторное создание главного ключа базы данных с обновлением до алгоритма шифрования AES необходимо произвести только один раз. Это никак не повлияет на последующие операции повторного создания, выполняемые в соответствии со стратегией смены ключей.  
  
## <a name="permissions"></a>Разрешения  
 Сведения о том, как обрабатываются разрешения при присоединении базы данных, см. в разделе [create database &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В данном примере происходит подключение файлов из базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] к текущему серверу.  
  
```  
EXEC sp_attach_db @dbname = N'AdventureWorks2012',   
    @filename1 =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_Data.mdf',   
    @filename2 =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_log.ldf';  
```  
  
## <a name="see-also"></a>См. также  
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
