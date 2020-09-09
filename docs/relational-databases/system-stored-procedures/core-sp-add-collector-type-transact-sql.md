---
description: core.sp_add_collector_type (Transact-SQL)
title: Core. sp_add_collector_type (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_collector_type
- sp_add_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- core.sp_add_collector_type stored procedure
- management data warehouse, data collector stored procedures
- sp_add_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 1d981037-2147-464e-a456-7d8e479bce89
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b9d907512edb385afba38b4ad1854a4535b67d9d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89536824"
---
# <a name="coresp_add_collector_type-transact-sql"></a>core.sp_add_collector_type (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Добавляет новую запись в представление core.supported_collector_types в базе данных (хранилище данных управления). Эта процедура должна выполняться в контексте базы данных хранилища данных управления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
core.sp_add_collector_type [ @collector_type_uid = ] 'collector_type_uid'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @collector_type_uid =] "*collector_type_uid*"  
 Идентификатор GUID типа сборщика. *collector_type_uid* имеет тип **uniqueidentifier**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **mdw_admin** (с разрешением EXECUTE).  
  
## <a name="examples"></a>Примеры  
 В следующем примере тип сборщика «Универсальный запрос T-SQL» добавляется в представление core.supported_collector_types. По умолчанию тип сборщика «Универсальный запрос T-SQL» уже существует. Поэтому если запустить этот код в экземпляре, установленном с параметрами по умолчанию, будет выведено сообщение о том, что тип сборщика уже существует.  
  
 Этот код будет выполнен успешно, если удалить тип сборщика «Универсальный запрос T-SQL» хранимой процедурой core.sp_remove_collector_type, а затем повторно добавить его в качестве зарегистрированного типа сборщика, который может передавать данные в хранилище данных управления.  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @RC int;  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = (SELECT collector_type_uid FROM msdb.dbo.syscollector_collector_types WHERE name = N'Generic T-SQL Query Collector Type');  
EXECUTE @RC = core.sp_add_collector_type @collector_type_uid;  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Хранилище данных управления](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
