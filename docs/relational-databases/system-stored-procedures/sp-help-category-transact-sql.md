---
description: sp_help_category (Transact-SQL)
title: sp_help_category (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_category
- sp_help_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_category
ms.assetid: 8cad1dcc-b43e-43bd-bea0-cb0055c84169
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d500bad167bda9085d4caf40bdaa9e442cb26efb
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549717"
---
# <a name="sp_help_category-transact-sql"></a>sp_help_category (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Выдает сведения об указанных классах заданий, предупреждений или операторов.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_category [ [ @class = ] 'class' ]   
     [ , [ @type = ] 'type' ]   
     [ , [ @name = ] 'name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @class = ] 'class'` Класс, для которого запрашиваются сведения. *класс* имеет тип **varchar (8)** и значение по умолчанию **Job**. *класс* может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**ДОЛЖНО**|Выдает сведения о категории заданий.|  
|**ПОЛУЧАЕТЕ**|Выдает сведения о категории предупреждений.|  
|**СТАНЦИИ**|Выдает сведения о категории операторов.|  
  
`[ @type = ] 'type'` Тип категории, для которой запрашиваются сведения. *Type имеет тип* **varchar (12)**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**LOCAL**|Категория локальных заданий.|  
|**MULTI -SERVER**|Категория многосерверных заданий.|  
|**NONE**|Категория для класса, отличного от **Job**.|  
  
`[ @name = ] 'name'` Имя категории, для которой запрашиваются сведения. Аргумент *Name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @suffix = ] suffix` Указывает, является ли столбец **category_type** в результирующем НАБОРе идентификатором или именем. *суффикс* имеет **битовую**длину и значение по умолчанию **0**. **1** показывает **category_type** как имя, а **0** — как идентификатор.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если ** \@ суффикс** равен **0**, **sp_help_category** возвращает следующий результирующий набор:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|Идентификатор категории|  
|**category_type**|**tinyint**|Тип категории:<br /><br /> **1** = локальный<br /><br /> **2** = многосерверная<br /><br /> **3** = нет|  
|**name**|**sysname**|Имя категории|  
  
 Если ** \@ суффикс** равен **1**, **sp_help_category** возвращает следующий результирующий набор:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|Идентификатор категории|  
|**category_type**|**sysname**|Тип категории. Один из нескольких **локальных**, **многосерверных**или **нет**|  
|**name**|**sysname**|Имя категории|  
  
## <a name="remarks"></a>Примечания  
 **sp_help_category** должны запускаться из базы данных **msdb** .  
  
 Если никакие аргументы не указаны, результирующий набор содержит сведения обо всех категориях заданий.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-local-job-information"></a>A. Возвращение сведений о локальных заданиях  
 В следующем примере возвращаются сведения о заданиях, администрируемых локально.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @type = N'LOCAL' ;  
GO  
```  
  
### <a name="b-returning-alert-information"></a>Б. Возвращение сведений о предупреждениях  
 В следующем примере возвращаются сведения о категории предупреждений Replication.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @class = N'ALERT',  
    @name = N'Replication' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_update_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
