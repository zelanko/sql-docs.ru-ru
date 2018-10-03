---
title: sys.database_recovery_status (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_recovery_status_TSQL
- database_recovery_status
- sys.database_recovery_status
- sys.database_recovery_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_recovery_status catalog view
ms.assetid: 46fab234-1542-49be-8edf-aa101e728acf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 72a292724a08917b18baedd6a3adbb8dfd00f739
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707352"
---
# <a name="sysdatabaserecoverystatus-transact-sql"></a>sys.database_recovery_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждой базы данных. Если база данных не открыта, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] предпринимает попытку запустить ее.  
  
 Для просмотра строки для базы данных, отличных от **master** или **tempdb**, необходимо применить, одно из следующих:  
  
-   Быть владельцем базы данных.  
  
-   Иметь разрешения уровня сервера ALTER ANY DATABASE или VIEW ANY DATABASE.  
  
-   Разрешение CREATE DATABASE **master** базы данных.    
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, уникальный внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**database_guid**|**uniqueidentifier**|Используется для связывания всех файлов базы данных. Чтобы база данных запускалась как ожидается, все ее файлы должны содержать этот идентификатор GUID в заголовочной странице. Только одна база данных должна иметь этот идентификатор GUID, но при копировании и прикреплении баз данных могут быть созданы копии. Инструкция RESTORE всегда формирует новый идентификатор GUID при восстановлении базы данных, которая еще не существует.<br /><br /> NULL = база данных находится в режиме вне сети либо не запущена.|  
|**family_guid**|**uniqueidentifier**|Идентификатор «семейства резервных копий» базы данных для определения совпадающих состояний восстановления.<br /><br /> NULL = база данных находится в режиме вне сети, либо не запущена.|  
|**last_log_backup_lsn**|**numeric(25,0)**|Начальный номер последовательности журнала следующей резервной копии журнала.<br /><br /> Если значение равно NULL, журнал транзакций обратно до невозможно выполнить, так как база данных находится в ПРОСТОЕ восстановление или нет текущей резервной копии базы данных.|  
|**recovery_fork_guid**|**uniqueidentifier**|Определяет текущую вилку восстановления, на которой в данной момент активна база данных.<br /><br /> NULL = база данных находится в режиме вне сети либо не запущена.|  
|**first_recovery_fork_guid**|**uniqueidentifier**|Идентификатор начальной вилки восстановления.<br /><br /> NULL = база данных находится в режиме вне сети либо не запущена.|  
|**fork_point_lsn**|**numeric(25,0)**|Если **first_recovery_fork_guid** не равно (! =) для **recovery_fork_guid**, **fork_point_lsn** является регистрационный номер текущей вилки. В противном случае значение равно NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталогов баз данных и файлов (Transact-SQL)](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [RESTORE HEADERONLY (Transact-SQL)](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
