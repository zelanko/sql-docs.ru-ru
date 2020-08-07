---
title: sp_add_category (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_category
- sp_add_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_category
ms.assetid: 6cca32cd-d941-4378-aed6-a7c90cb7520a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 323a86b4efbaa63d8858341c68908e30258d4889
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87865292"
---
# <a name="sp_add_category-transact-sql"></a>sp_add_category (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Добавляет указанную категорию заданий, предупреждений или операторов на сервер. Альтернативный способ см. в разделе [Создание категории заданий с помощью SQL Server Management Studio](/sql/ssms/agent/create-a-job-category).
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
 > [!IMPORTANT]  
 > В [Azure SQL управляемый экземпляр](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), в настоящее время поддерживаются не все функции агент SQL Server. Дополнительные сведения см. [в статье отличия T-sql управляемый экземпляр SQL Azure от SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) .
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_category   
     [ [ @class = ] 'class', ]   
     [ [ @type = ] 'type', ]   
     { [ @name = ] 'name' }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @class = ] 'class'`Класс добавляемой категории. *класс* имеет тип **varchar (8)** со ЗНАЧЕНИЕМ по умолчанию Job и может принимать одно из следующих значений.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|JOB|Добавление категории заданий.|  
|ALERT|Добавление категории предупреждений.|  
|OPERATOR|Добавление категории операторов.|  
  
`[ @type = ] 'type'`Тип добавляемой категории. *тип* — **varchar (12)**, со значением по умолчанию **Local**и может принимать одно из следующих значений.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|LOCAL|Локальная категория заданий.|  
|НЕСКОЛЬКО СЕРВЕРОВ|Многосерверная категория заданий.|  
|None|Категория для класса, отличного от JOB **.**|  
  
`[ @name = ] 'name'`Имя добавляемой категории. Имя должно быть уникальным в указанном классе. Аргумент *Name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_add_category** должны запускаться из базы данных **msdb** .  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_add_category**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается локальная категория заданий с именем `AdminJobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_category  
    @class=N'JOB',  
    @type=N'LOCAL',  
    @name=N'AdminJobs' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_delete_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_help_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [sp_update_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [dbo.sysзадания &#40;&#41;Transact-SQL](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md)   
 [dbo.sysжобсерверс &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
