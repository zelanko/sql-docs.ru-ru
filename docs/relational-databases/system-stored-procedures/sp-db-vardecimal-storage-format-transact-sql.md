---
title: "sp_db_vardecimal_storage_format (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_db_vardecimal_storage_format
- sp_db_vardecimal_storage_format_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_db_vardecimal_storage_format
- decimal data type, compressing
- compressing decimal data
- numeric data type, compressing
- database compression [SQL Server]
- table compression [SQL Server]
ms.assetid: 9920b2f7-b802-4003-913c-978c17ae4542
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4ff2ceb2a1e5a616ed12815b678fca6e978a308
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spdbvardecimalstorageformat-transact-sql"></a>sp_db_vardecimal_storage_format (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает текущее состояние формата хранения vardecimal для базы данных либо включает этот формат в базе данных.  Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], пользовательские базы данных всегда включены. Включение формата хранения vardecimal для баз данных необходимо только в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
> [!IMPORTANT]  
>  Изменение состояния формата хранения vardecimal для базы данных может повлиять на резервное копирование и восстановление, зеркальное отображение базы данных, sp_attach_db, доставку журналов и репликацию.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_db_vardecimal_storage_format [ [ @dbname = ] 'database_name']   
    [ , [ @vardecimal_storage_format = ] { 'ON' | 'OFF' } ]   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @dbname=] '*имя_базы_данных*"  
 Имя базы данных, формат хранения которой нужно изменить. *database_name* — **sysname**, не имеет значения по умолчанию. Если имя базы данных пропущено, то возвращаются состояния формата хранения vardecimal для всех баз данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [ @vardecimal_storage_format=] {«ON» | " ОТКЛЮЧЕНИЕ "}  
 Указывает, включен ли формат хранения vardecimal. Аргумент @vardecimal_storage_format может иметь значение ON или OFF. Параметр — **тип varchar(3) столбцы разделяются**, не имеет значения по умолчанию. Если имя базы данных указано, но аргумент @vardecimal_storage_format пропущен, то возвращается текущий параметр указанной базы данных. Этот аргумент не действует в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздних версиях.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если формат хранения базы данных изменить нельзя, то хранимая процедура sp_db_vardecimal_storage_format возвращает ошибку. Если база данных уже находится в указанном состоянии, то хранимая процедура не вносит никаких изменений.  
  
 Если @vardecimal_storage_format аргумент не указан, возвращаются столбцы, имя базы данных и Vardecimal State.  
  
## <a name="remarks"></a>Замечания  
 Процедура sp_db_vardecimal_storage_format возвращает состояние vardecimal, но не может изменить его.  
  
 Хранимая процедура sp_db_vardecimal_storage_format завершается неуспешно в следующих случаях:  
  
-   Отсутствуют активные пользователи базы данных.  
  
-   Включено зеркальное отображение базы данных.  
  
-   Выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает формат хранения vardecimal.  
  
 Чтобы изменить состояние формата хранения vardecimal на OFF, необходимо переключить базу данных на простую модель восстановления. При переключении базы данных на простую модель восстановления цепочка журналов прерывается. После переключения состояния формата хранения vardecimal на OFF следует создать полную резервную копию базы данных.  
  
 Переключение в состояние OFF не будет выполнено, если в таблицах используется сжатие баз данных vardecimal. Чтобы изменить формат хранения таблицы, используйте [sp_tableoption](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Определить, в каких таблицах базы данных используется формат хранения vardecimal, можно с помощью функции `OBJECTPROPERTY` и поиском свойства `TableHasVarDecimalStorageFormat`, как показано в приведенном ниже примере.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT name, object_id, type_desc  
FROM sys.objects   
 WHERE OBJECTPROPERTY(object_id,   
   N'TableHasVarDecimalStorageFormat') = 1 ;  
GO  
```  
  
## <a name="examples"></a>Примеры  
 В следующем коде включается сжатие в базе данных `AdventureWorks2012`, подтверждается состояние, а затем сжимаются десятичные и числовые столбцы в таблице `Sales.SalesOrderDetail`.  
  
```  
USE master ;  
GO  
  
EXEC sp_db_vardecimal_storage_format 'AdventureWorks2012', 'ON' ;  
GO  
  
-- Check the vardecimal storage format state for  
-- all databases in the instance.  
EXEC sp_db_vardecimal_storage_format ;  
GO  
  
USE AdventureWorks2012 ;  
GO  
  
EXEC sp_tableoption 'Sales.SalesOrderDetail', 'vardecimal storage format', 1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Компонент Database Engine хранимой процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
