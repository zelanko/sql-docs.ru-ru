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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1b5dfd9cf062e5767606d83c3beb8a25b36387f1
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538226"
---
# <a name="spdetachdb-transact-sql"></a>sp_detach_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
`[ @dbname = ] 'database_name'` — Имя базы данных для отсоединения. *database_name* — **sysname** значение со значением по умолчанию NULL.  
  
`[ @skipchecks = ] 'skipchecks'` Указывает, следует ли пропустить, или выполните обновление СТАТИСТИКИ. *параметром skipchecks* — **nvarchar(10)** значение со значением по умолчанию NULL. Чтобы выполнять инструкцию UPDATE STATISTICS, укажите **true**. Чтобы явно запустить инструкцию UPDATE STATISTICS, укажите **false**.  
  
 По умолчанию инструкция UPDATE STATISTICS запускается для обновления информации о данных в таблицах и индексах. Выполнение UPDATE STATISTICS имеет смысл для тех баз данных, которые планируется переместить на постоянные носители информации.  
  
`[ @keepfulltextindexfile = ] 'KeepFulltextIndexFile'` Указывает, что файл полнотекстового индекса, связанный с, отключаемой базы данных не будет удален во время базы данных операции отсоединения. *KeepFulltextIndexFile* — **nvarchar(10)** значение по умолчанию **true**. Если *KeepFulltextIndexFile* — **false**, все файлы полнотекстового индекса, связанные с базой данных и метаданные полнотекстового индекса удаляются, если она доступна только для чтения. Если значение равно NULL или **true**, связанного с полнотекстовым поиском, хранятся в метаданных.  
  
> [!IMPORTANT]
>  **@keepfulltextindexfile** Параметр будет удален в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не используйте его при работе над новыми приложениями и как можно быстрее измените приложения, в которых он в настоящее время используется.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 При отсоединении базы данных все метаданные удаляются. Если база данных была база данных по умолчанию для учетной записи входа, **master** становится базой данных по умолчанию.  
  
> [!NOTE]  
>  Сведения о просмотре базы данных по умолчанию для всех учетных записей входа см. в разделе [sp_helplogins &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md). Если у вас есть необходимые разрешения, можно использовать [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) для назначения новой базы данных по умолчанию для имени входа.  
  
## <a name="restrictions"></a>Ограничения  
 Невозможно отсоединить базу данных, если выполняется одно из следующих условий:  
  
-   База данных в настоящий момент используется. Дополнительные сведения см. ниже в разделе «Получение монопольного доступа».  
  
-   При репликации база данных публикуется.  
  
     Перед отсоединением базы данных, необходимо отключить публикацию, выполнив [sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md).  
  
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
  
 Например, следующая `ALTER DATABASE` инструкция получает монопольный доступ к [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных после отключения всех текущих пользователей из базы данных.  
  
```  
USE master;  
ALTER DATABASE AdventureWorks2012  
SET SINGLE_USER;  
GO  
```  
  
> [!NOTE]  
>  Чтобы принудительно отключить текущих пользователей от базы данных, немедленно или через указанное число секунд, используйте параметр ROLLBACK: ALTER DATABASE *имя_базы_данных* SET SINGLE_USER WITH ROLLBACK *rollback_option*. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="reattaching-a-database"></a>Повторное присоединение базы данных  
 Отсоединенные файлы останутся на диске и могут быть повторно подсоединены с помощью вызова CREATE DATABASE (с параметрами FOR ATTACH или FOR ATTACH_REBUILD_LOG). Файлы можно также переместить на другой сервер и подсоединить там.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** предопределенной роли сервера или членство в **db_owner** роль базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере отсоединяется [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных с помощью *параметром skipchecks* задано значение true.  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
 В следующем примере отсоединяется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] и сохраняются файлы полнотекстового индекса и метаданные полнотекстового индекса. Эта команда выполняет инструкцию UPDATE STATISTICS — такое поведение установлено по умолчанию.  
  
```  
exec sp_detach_db @dbname='AdventureWorks2012'  
    , @keepfulltextindexfile='true';  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Отсоединение базы данных](../../relational-databases/databases/detach-a-database.md)  
  
  
