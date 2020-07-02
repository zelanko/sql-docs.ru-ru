---
title: sp_detach_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/30/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_detach_db
- sp_detach_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_detach_db
- detaching databases [SQL Server]
ms.assetid: abcb1407-ff78-4c76-b02e-509c86574462
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d9eaae9a00a125a2ffe2f290e2bd772eb40d84c6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717352"
---
# <a name="sp_detach_db-transact-sql"></a>sp_detach_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Отсоединяет неиспользуемую базу данных от экземпляра сервера и (необязательно) выполняет инструкцию UPDATE STATISTICS для всех таблиц перед отключением.  
  
> [!IMPORTANT]  
>  Перед отсоединением реплицируемой базы данных ее публикация должна быть прекращена. Дополнительные сведения см. в подразделе «Замечания» далее в этом разделе.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_detach_db [ @dbname= ] 'database_name'   
    [ , [ @skipchecks= ] 'skipchecks' ]   
    [ , [ @keepfulltextindexfile = ] 'KeepFulltextIndexFile' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'database_name'`Имя базы данных, подсоединяемой. *database_name* имеет значение типа **sysname** и значение по умолчанию NULL.  
  
`[ @skipchecks = ] 'skipchecks'`Указывает, следует ли пропустить или выполнить обновление статистики. *параметром skipchecks установленным* — это значение типа **nvarchar (10)** со ЗНАЧЕНИЕМ по умолчанию NULL. Чтобы пропустить СТАТИСТИКУ обновления, укажите **значение true**. Чтобы явно выполнить обновление статистики, укажите **значение false**.  
  
 По умолчанию инструкция UPDATE STATISTICS запускается для обновления информации о данных в таблицах и индексах. Выполнение UPDATE STATISTICS имеет смысл для тех баз данных, которые планируется переместить на постоянные носители информации.  
  
`[ @keepfulltextindexfile = ] 'KeepFulltextIndexFile'`Указывает, что файл полнотекстового индекса, связанный с отсоединяемой базой данных, не будет удален во время операции отсоединения базы данных. *KeepFulltextIndexFile* — это значение типа **nvarchar (10)** со значением по умолчанию **true**. Если *KeepFulltextIndexFile* имеет **значение false**, все файлы полнотекстовых индексов, связанные с базой данных, и метаданные полнотекстового индекса удаляются, если только база данных не доступна только для чтения. Если задано значение NULL или **true**, метаданные, связанные с полнотекстовым текстом, сохраняются.  
  
> [!IMPORTANT]
>  Параметр ** \@ KeepFulltextIndexFile** будет удален в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Не используйте его при работе над новыми приложениями и как можно быстрее измените приложения, в которых он в настоящее время используется.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 При отсоединении базы данных все метаданные удаляются. Если база данных была базой данных по умолчанию для любых учетных записей входа, база данных **master** станет базой по умолчанию.  
  
> [!NOTE]  
>  Сведения о том, как просмотреть базу данных по умолчанию для всех учетных записей входа, см. в разделе [sp_helplogins &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md). При наличии необходимых разрешений можно использовать [инструкцию ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) , чтобы назначить имя входа новой базе данных по умолчанию.  
  
## <a name="restrictions"></a>Ограничения  
 Невозможно отсоединить базу данных, если выполняется одно из следующих условий:  
  
-   База данных в настоящий момент используется. Дополнительные сведения см. ниже в разделе «Получение монопольного доступа».  
  
-   При репликации база данных публикуется.  
  
     Прежде чем можно будет отсоединить базу данных, необходимо отключить публикацию, выполнив [sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md).  
  
    > [!NOTE]  
    >  Если невозможно использовать процедуру **sp_replicationdboption**, можно удалить репликацию, выполнив процедуру [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md).  
  
-   Имеется моментальный снимок базы данных.  
  
     Перед отсоединением базы данных необходимо удалить все моментальные снимки. Дополнительные сведения см. в разделе [Удаление моментального снимка базы данных (Transact-SQL)](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md).  
  
    > [!NOTE]  
    >  Невозможно отсоединить или присоединить моментальный снимок базы данных.  
  
-   Выполняется зеркальное отображение базы данных.  
  
     Отключить базу данных невозможно, пока этот процесс не завершится. Дополнительные сведения см. в разделе [Удаление зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md).  
  
-   База данных помечена как подозрительная.  
  
     Подозрительную базу данных необходимо перевести в аварийный режим перед ее отсоединением. Дополнительные сведения о переводе базы данных в аварийный режим см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
-   База данных является системной базой данных.  
  
## <a name="obtaining-exclusive-access"></a>Получение монопольного доступа  
 Для отсоединения базы данных требуется монопольный доступ к ней. Если база данных, которую необходимо отключить, используется в настоящий момент, следует переключить ее в режим SINGLE_USER для получения монопольного доступа.

 Перед заданием параметра SINGLE_USER проверьте, чтобы параметру AUTO_UPDATE_STATISTICS_ASYNC было присвоено значение OFF. Если этот параметр имеет значение ON, то фоновый поток, используемый для обновления статистики, соединится с базой данных и доступ к базе данных в однопользовательском режиме будет невозможен. Дополнительные сведения см. в разделе [Установка однопользовательского режима базы данных](../databases/set-a-database-to-single-user-mode.md).

 Например, следующая `ALTER DATABASE` инструкция получает монопольный доступ к [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базе данных после отключения всех текущих пользователей от базы данных.  
  
```  
USE master;  
ALTER DATABASE AdventureWorks2012  
SET SINGLE_USER;  
GO  
```  
  
> [!NOTE]  
>  Для принудительной установки текущих пользователей из базы данных немедленно или в течение заданного количества секунд также используйте параметр ROLLBACK: ALTER DATABASE *database_name* Set SINGLE_USER WITH ROLLBACK *rollback_option*. Дополнительные сведения см. в разделе [ALTER database &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="reattaching-a-database"></a>Повторное присоединение базы данных  
 Отсоединенные файлы останутся на диске и могут быть повторно подсоединены с помощью вызова CREATE DATABASE (с параметрами FOR ATTACH или FOR ATTACH_REBUILD_LOG). Файлы можно также переместить на другой сервер и подсоединить там.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **sysadmin** или членство в роли **db_owner** базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере база данных отсоединяется [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] с параметром *параметром skipchecks установленным* , для которого задано значение true.  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
 В следующем примере отсоединяется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] и сохраняются файлы полнотекстового индекса и метаданные полнотекстового индекса. Эта команда выполняет инструкцию UPDATE STATISTICS — такое поведение установлено по умолчанию.  
  
```  
exec sp_detach_db @dbname='AdventureWorks2012'  
    , @keepfulltextindexfile='true';  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Отсоединение базы данных](../../relational-databases/databases/detach-a-database.md)  
  
  
