---
title: sp_dropextendedproperty (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropextendedproperty_TSQL
- sp_dropextendedproperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproperty
ms.assetid: 4851865a-86ca-4823-991a-182dd1934075
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e01b14407198ed88654527bd247a116c200fb1e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627432"
---
# <a name="spdropextendedproperty-transact-sql"></a>sp_dropextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет существующие расширенные свойства.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropextendedproperty   
    [ @name = ] { 'property_name' }  
      [ , [ @level0type = ] { 'level0_object_type' }   
        , [ @level0name = ] { 'level0_object_name' }   
            [ , [ @level1type = ] { 'level1_object_type' }   
              , [ @level1name = ] { 'level1_object_name' }   
                [ , [ @level2type = ] { 'level2_object_type' }   
                  , [ @level2name = ] { 'level2_object_name' }   
                ]   
            ]   
        ]   
    ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @name=] {"*property_name*"}  
 Имя свойства, которое необходимо удалить. *property_name* — **sysname** и не может иметь значение NULL.  
  
 [ @level0type=] {"*level0_object_type*"}  
 Имя указанного типа объекта уровня 0. *level0_object_type* — **varchar(128)**, значение по умолчанию NULL.  
  
 Допустимые входные данные: ASSEMBLY, CONTRACT, EVENT NOTIFICATION, FILEGROUP, MESSAGE TYPE, PARTITION FUNCTION, PARTITION SCHEME, REMOTE SERVICE BINDING, ROUTE, SCHEMA, SERVICE, USER, TRIGGER, TYPE и NULL.  
  
> [!IMPORTANT]  
>  Типы USER и TYPE уровня 0 будут удалены в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время. Тип SCHEMA следует использовать в качестве типа уровня 0 вместо USER. В значении аргумента TYPE следует указывать тип SCHEMA в качестве типа уровня 0 и TYPE в качестве типа уровня 1.  
  
 [ @level0name=] {"*level0_object_name*"}  
 Имя указанного типа объекта уровня 0. *level0_object_name* — **sysname** значение по умолчанию NULL.  
  
 [ @level1type=] {"*level1_object_type*"}  
 Тип объекта уровня 1. *level1_object_type* — **varchar(128)** значение по умолчанию NULL. Допустимые входные данные: AGGREGATE, DEFAULT, FUNCTION, LOGICAL FILE NAME, PROCEDURE, QUEUE, RULE, SYNONYM, TABLE, TABLE_TYPE, TYPE, VIEW, XML SCHEMA COLLECTION и NULL.  
  
 [ @level1name=] {"*level1_object_name*"}  
 Имя указанного типа объекта уровня 1. *level1_object_name* — **sysname** значение по умолчанию NULL.  
  
 [ @level2type=] {"*level2_object_type*"}  
 Тип объекта уровня 2. *level2_object_type* — **varchar(128)** значение по умолчанию NULL. Допустимые входные данные: COLUMN, CONSTRAINT, EVENT NOTIFICATION, INDEX, PARAMETER, TRIGGER и NULL.  
  
 [ @level2name=] {"*level2_object_name*"}  
 Имя указанного типа объекта уровня 2. *level2_object_name* — **sysname** значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 С целью указания расширенных свойств объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных распределены по трем уровням: 0, 1 и 2. Уровень 0 является высшим уровнем и определяется как «объекты в области базы данных». Объекты уровня 1 содержатся в схеме и в пользовательской области, а объекты уровня 2 содержатся в объектах уровня 1. Расширенные свойства могут быть определены для объектов на любом из этих уровней. Ссылки на объект определенного уровня должны снабжаться типами и именами всех объектов вышестоящих уровней.  
  
 Задан допустимый *property_name*, если все типы и имена объектов имеют значение null, и свойство существует в текущей базе данных, что свойство удаляется. См. пример Б далее в этом разделе.  
  
## <a name="permissions"></a>Разрешения  
 Члены предопределенной роли базы данных db_ddladmin и db_owner могут удалять расширенные свойства любого объекта за следующим исключением: db_ddladmin не могут добавлять свойства к самой базе данных, пользователям или ролям.  
  
 Пользователи могут удалять расширенные свойства объектов, которыми они владеют или на которые у них есть разрешения ALTER или CONTROL.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-an-extended-property-on-a-column"></a>A. Удаление расширенного свойства столбца  
 В следующем примере удаляется свойство `caption` столбца `id` таблицы `T1`, находящейся в схеме `dbo`.  
  
```  
CREATE TABLE T1 (id int , name char (20));  
GO  
EXEC sp_addextendedproperty   
     @name = 'caption'   
    ,@value = 'Employee ID'   
    ,@level0type = 'schema'   
    ,@level0name = dbo  
    ,@level1type = 'table'  
    ,@level1name = 'T1'  
    ,@level2type = 'column'  
    ,@level2name = id;  
GO  
EXEC sp_dropextendedproperty   
     @name = 'caption'   
    ,@level0type = 'schema'   
    ,@level0name = dbo  
    ,@level1type = 'table'  
    ,@level1name = 'T1'  
    ,@level2type = 'column'  
    ,@level2name = id;  
GO  
DROP TABLE T1;  
GO  
```  
  
### <a name="b-dropping-an-extended-property-on-a-database"></a>Б. Удаление расширенного свойства базы данных  
 В следующем примере удаляется свойство с именем `MS_Description` из [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] образца базы данных. Так как это свойство относится к самой базе данных, типы и имена объектов не указываются.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_dropextendedproperty   
@name = N'MS_Description';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.fn_listextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)   
 [sys.extended_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
