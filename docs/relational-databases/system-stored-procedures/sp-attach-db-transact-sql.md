---
title: sp_attach_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_attach_db_TSQL
- sp_attach_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_db
ms.assetid: 59bc993e-7913-4091-89cb-d2871cffda95
caps.latest.revision: 69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1c275128a8e3c2bbce6165486e256fc5b34d402d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38037202"
---
# <a name="spattachdb-transact-sql"></a>sp_attach_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Присоединение базы данных к серверу.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Мы рекомендуем использовать инструкцию CREATE DATABASE *имя_базы_данных* FOR ATTACH вместо этого. Дополнительные сведения см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
> [!NOTE]  
>  Чтобы перестроить несколько файлов журналов, когда один или несколько имеют новое расположение, использовать инструкцию CREATE DATABASE *имя_базы_данных* FOR ATTACH_REBUILD_LOG.  
  
> [!IMPORTANT]  
>  Не рекомендуется подключать или восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_attach_db [ @dbname= ] 'dbname'  
    , [ @filename1= ] 'filename_n' [ ,...16 ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@dbname=** ] **"*** dbnam* **"**  
 Имя базы данных, присоединяемой к серверу. Имя должно быть уникальным. *DBName* — **sysname**, значение по умолчанию NULL.  
  
 [ **@filename1=** ] **'***filename_n***'**  
 Это физическое имя файла базы данных, содержащее путь к каталогу. *filename_n* — **nvarchar(260)**, значение по умолчанию NULL. Можно указать до 16 имен файлов. Имена параметров начинаются с **@filename1** и возрастают до **@filename16**. Список имен файлов должен включать хотя бы первичный файл. Первичный файл содержит системные таблицы, указывающие на другие файлы базы данных. Список также должен включать все файлы, перемещенные после отключения базы данных.  
  
> [!NOTE]  
>  Этот аргумент сопоставляется с параметром FILENAME инструкции CREATE DATABASE. Дополнительные сведения см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
>   
>  Когда базу данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с файлами полнотекстовых каталогов присоединяют к экземпляру сервера [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , то присоединение файлов каталогов выполняется из их предыдущего расположения вместе с другими файлами баз данных, как и в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения см. в разделе [Обновление полнотекстового поиска](../../relational-databases/search/upgrade-full-text-search.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **Sp_attach_db** хранимая процедура должна выполняться только в базах данных, которые были предварительно отсоединены от сервера базы данных с помощью явной **sp_detach_db** операции или на скопированных базах данных. Если вам нужно указать более 16 файлов, использовать инструкцию CREATE DATABASE *имя_базы_данных* FOR ATTACH или CREATE DATABASE *имя_базы_данных* FOR_ATTACH_REBUILD_LOG. Дополнительные сведения см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
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
 Сведения об управлении разрешениями при присоединении базы данных, см. в разделе [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
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
 [sp_detach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_removedbreplication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
