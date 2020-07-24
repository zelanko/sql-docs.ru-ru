---
title: sp_clean_db_file_free_space (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_clean_db_file_free_space
- sp_clean_db_file_free_space_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ghost records
- sp_clean_db_file_free_space
ms.assetid: 3eb53a67-969d-4cb8-9681-b1c8e6fd55b6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d8c45d25dd63149145fc732642b873bc4e7a6193
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2020
ms.locfileid: "87122495"
---
# <a name="sp_clean_db_file_free_space-transact-sql"></a>sp_clean_db_file_free_space (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет остаточные данные, оставляемые на страницах базы данных процедурами изменения данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. sp_clean_db_file_free_space очищает все страницы только в одном файле базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql  
sp_clean_db_file_free_space   
  [ @dbname = ] 'database_name'   
  , [ @fileid = ] 'file_number'   
  [ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 @dbname= '*database_name*'  
 Имя очищаемой базы данных. Аргумент *dbname* имеет тип **sysname** и не может иметь значение null.  
  
 @fileid= '*file_number*'  
 Идентификатор очищаемого файла данных. *file_number* имеет **тип int** и не может иметь значение null.  
  
 @cleaning_delay= '*delay_in_seconds*'  
 Интервал задержки между операциями очистки страниц. Применение задержки помогает уменьшить нагрузку на систему ввода-вывода. *delay_in_seconds* имеет **тип int** и значение по умолчанию 0.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Комментарии  
 Удаляет операции из таблицы или обновляет операции, которые приводят к перемещению строки, что может немедленно освободить пространство на странице путем удаления ссылок на строку. Но при определенных обстоятельствах строка может физически оставаться на странице данных как фантомная запись. Фантомные записи периодически удаляются фоновым процессом. Эти остаточные данные не возвращаются [!INCLUDE[ssDE](../../includes/ssde-md.md)] в ответ на запросы. Однако в средах, в которых физическая безопасность данных или файлов резервных копий находится под угрозой, можно использовать `sp_clean_db_file_free_space` для очистки этих фантомных записей. Чтобы выполнить эту операцию для всех файлов базы данных одновременно, используйте [sp_clean_db_free_space (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-clean-db-free-space-transact-sql.md). 
  
 Продолжительность времени, необходимого для выполнения процедуры sp_clean_db_file_free_space, зависит от размера файла, доступного свободного пространства и емкости диска. Поскольку работа `sp_clean_db_file_free_space` может значительно повлиять на операции ввода-вывода, рекомендуется выполнять эту процедуру за пределами обычных часов работы.  
  
 Перед запуском `sp_clean_db_file_free_space` рекомендуется создать полную резервную копию базы данных.  
  
 Связанная [sp_clean_db_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-free-space-transact-sql.md) хранимая процедура очищает все файлы в базе данных.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в `db_owner` роли базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется очистка всех остаточных данных в первичном файле данных базы данных `AdventureWorks2012`.  
  
```sql  
USE master;  
GO  
EXEC sp_clean_db_file_free_space @dbname = N'AdventureWorks2012', @fileid = 1;  
```  
  
## <a name="see-also"></a>См. также  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Обзор процесса очистки фантомных записей](../ghost-record-cleanup-process-guide.md)    
 [sp_clean_db_free_space (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-clean-db-free-space-transact-sql.md)
   
