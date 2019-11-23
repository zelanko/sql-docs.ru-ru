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
ms.openlocfilehash: 076d5ade1f4951183578b1b46761d49dafbce8be
ms.sourcegitcommit: df1f71231f8edbdfe76e8851acf653c25449075e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2019
ms.locfileid: "70810551"
---
# <a name="sp_add_category-transact-sql"></a>sp_add_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Добавляет указанную категорию заданий, предупреждений или операторов на сервер. Альтернативный способ см. в разделе [Создание категории заданий с помощью SQL Server Management Studio](/sql/ssms/agent/create-a-job-category).
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
 > [!IMPORTANT]  
 > Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_category   
     [ [ @class = ] 'class', ]   
     [ [ @type = ] 'type', ]   
     { [ @name = ] 'name' }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @class = ] 'class'` класс добавляемой категории. *класс* имеет тип **varchar (8)** со ЗНАЧЕНИЕМ по умолчанию Job и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|JOB|Добавление категории заданий.|  
|ALERT|Добавление категории предупреждений.|  
|OPERATOR|Добавление категории операторов.|  
  
`[ @type = ] 'type'` тип добавляемой категории. *тип* — **varchar (12)** , со значением по умолчанию **Local**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|LOCAL|Локальная категория заданий.|  
|НЕСКОЛЬКО СЕРВЕРОВ|Многосерверная категория заданий.|  
|None|Категория для класса, отличного от JOB **.**|  
  
`[ @name = ] 'name'` имя добавляемой категории. Имя должно быть уникальным в указанном классе. Аргумент *Name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
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
  
## <a name="see-also"></a>См. также статью  
 [sp_delete_category &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)  
 [sp_help_category &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)  
 [sp_update_category &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)  
   [Transact- &#40;SQL&#41; в dbo. sysjobs](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md)  
   [Transact- &#40;SQL&#41; в dbo. сисжобсерверс](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
