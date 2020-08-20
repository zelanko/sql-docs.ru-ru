---
description: sp_can_tlog_be_applied (Transact-SQL)
title: sp_can_tlog_be_applied (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_can_tlog_be_applied_TSQL
- sp_can_tlog_be_applied
dev_langs:
- TSQL
helpviewer_keywords:
- sp_can_tlog_be_applied
ms.assetid: 9c143b6c-27ac-4ab7-98d1-3b7b265f3963
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4e4596cfab5bb7a272e29b2d2749e38c9f38ddaf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464483"
---
# <a name="sp_can_tlog_be_applied-transact-sql"></a>sp_can_tlog_be_applied (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Проверяет, может ли резервная копия журнала транзакций применяться к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **sp_can_tlog_be_applied** требует, чтобы база данных была в состоянии восстановления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_can_tlog_be_applied [ @backup_file_name = ] 'backup_file_name'   
        , [ @database_name = ] 'database_name'   
        , [ @result = ] result OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @backup_file_name = ] 'backup_file_name'` Имя файла резервной копии. *backup_file_name* имеет тип **nvarchar (128)**.  
  
`[ @database_name = ] 'database_name'` Имя базы данных. Аргумент *database_name* имеет тип **sysname**.  
  
`[ @result = ] _result_ OUTPUT` Указывает, можно ли применить журнал транзакций к базе данных. *результат* является **битом**.  
  
 1 = журнал может быть применен;  
  
 0= Журнал не может быть применен.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_can_tlog_be_applied**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере для хранения результата задается переменная `@MyBitVar`.  
  
```  
USE master;  
GO  
DECLARE @MyBitVar BIT;  
EXEC sp_can_tlog_be_applied  
     @backup_file_name =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\AdventureWorks2012.bak',  
     @database_name = N'AdventureWorks2012',  
     @result = @MyBitVar OUTPUT;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
