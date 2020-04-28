---
title: managed_backup. fn_get_parameter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_get_parameter_TSQL
- smart_admin.fn_get_parameter
- fn_get_parameter_TSQL
- fn_get_parameter
dev_langs:
- TSQL
helpviewer_keywords:
- fn_get_parameter
- smart_admin.fn_get_parameter
ms.assetid: ed94e54d-4516-4806-a8ce-f013d3a04122
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18a42273218bb73de55694b9b54877a4f2e0f669
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68140649"
---
# <a name="managed_backupfn_get_parameter-transact-sql"></a>managed_backup. fn_get_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает таблицу из 0, 1 или более строк пар «параметр-значение».  
  
 Используйте эту хранимую процедуру для просмотра всех или определенных параметров конфигурации для Smart Admin.  
  
 Если параметр еще никогда не был настроен, функция возвращает 0 строк.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
managed_backup.fn_get_parameter ('parameter_name' | '' | NULL )  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Даваемых  
 parameter_name  
 Имя параметра. parameter_name имеет тип **nvarchar (128)**. Если в качестве аргумента этой функции предоставляется NULL или пустая строка, возвращаются пары «имя-значение» для всех настроенных параметров Smart Admin.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|parameter_name|NVARCHAR(128)|Имя параметра. Ниже приведен текущий список возвращаемых параметров.<br/><br/>**филеретентиондебугксевент**<br/><br/>**SSMBackup2WADebugXevent**<br/><br/>**SSMBackup2WANotificationEmailIds**<br/><br/>**SSMBackup2WAEnableUserDefinedPolicy**<br/><br/>**SSMBackup2WAEverConfigured**<br/><br/>**сторажеоператиондебугксевент**|  
|parameter_value|NVARCHAR(128)|Текущее заданное значение параметра.|  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимы разрешения SELECT для функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все параметры, настроенные хотя бы один раз, и их текущие значения.  
  
```  
USE MSDB  
GO  
SELECT *   
FROM managed_backup.fn_get_parameter (NULL)  
  
```  
  
 Следующий пример возвращает адрес электронной почты, указанный, чтобы получать уведомления об ошибках. Если строки не возвращаются, значит функция уведомления по электронной почте не включена.  
  
```  
USE MSDB  
GO  
SELECT *  
FROM managed_backup.fn_get_parameter ('SSMBackup2WANotficationEmailIds')  
  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server управляемого резервного копирования Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
