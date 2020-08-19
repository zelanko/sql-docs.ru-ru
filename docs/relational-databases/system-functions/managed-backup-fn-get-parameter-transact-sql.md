---
description: managed_backup. fn_get_parameter (Transact-SQL)
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
ms.openlocfilehash: da8c646cca92a5ef25fd12322fd8a6bd222a1c9e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419518"
---
# <a name="managed_backupfn_get_parameter-transact-sql"></a>managed_backup. fn_get_parameter (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Возвращает таблицу из 0, 1 или более строк пар «параметр-значение».  
  
 Используйте эту хранимую процедуру для просмотра всех или определенных параметров конфигурации для Smart Admin.  
  
 Если параметр еще никогда не был настроен, функция возвращает 0 строк.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
managed_backup.fn_get_parameter ('parameter_name' | '' | NULL )  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a> Аргументы  
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
 [Управляемое резервное копирование SQL Server в Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
