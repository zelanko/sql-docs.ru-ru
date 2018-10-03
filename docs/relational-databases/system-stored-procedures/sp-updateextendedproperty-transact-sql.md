---
title: sp_updateextendedproperty (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/12/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_updateextendedproperty_TSQL
- sp_updateextendedproperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updateextendedproperty
ms.assetid: 7f02360f-cb9e-48b4-b75f-29b4bc9ea304
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 347e8d170006cb289b421171851140b18e64f14b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843852"
---
# <a name="spupdateextendedproperty-transact-sql"></a>sp_updateextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Обновляет значение существующего расширенного свойства.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_updateextendedproperty  
    [ @name = ]{ 'property_name' }   
    [ , [ @value = ]{ 'value' }  
        [, [ @level0type = ]{ 'level0_object_type' }  
         , [ @level0name = ]{ 'level0_object_name' }  
              [, [ @level1type = ]{ 'level1_object_type' }  
               , [ @level1name = ]{ 'level1_object_name' }  
                     [, [ @level2type = ]{ 'level2_object_type' }  
                      , [ @level2name = ]{ 'level2_object_name' }  
                     ]  
              ]  
        ]  
    ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @name=] {"*property_name*"}  
 Имя свойства, которое необходимо обновить. *property_name* — **sysname**, и не может иметь значение NULL.  
  
 [ @value=] {"*значение*"}  
 Значение, связанное со свойством. *значение* — **sql_variant**, значение по умолчанию NULL. Размер *значение* может оказаться более чем 7 500 байт.  
  
 [ @level0type=] {"*level0_object_type*"}  
 Пользователь или тип, определяемый пользователем. *level0_object_type* — **varchar(128)**, значение по умолчанию NULL. Допустимыми входными значениями являются сборки, КОНТРАКТА, уведомления о СОБЫТИИ, файловой группы, тип сообщений, функции СЕКЦИОНИРОВАНИЯ, СХЕМЫ СЕКЦИОНИРОВАНИЯ, СТРУКТУРЫ ПЛАНА, REMOTE SERVICE BINDING, МАРШРУТА, СХЕМЫ, службы, пользователя, триггер, тип и значение NULL.  
  
> [!IMPORTANT]  
>  Типы USER и TYPE уровня 0 будут удалены в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время. Тип SCHEMA следует использовать в качестве типа уровня 0 вместо USER. В значении аргумента TYPE следует указывать тип SCHEMA в качестве типа уровня 0 и TYPE в качестве типа уровня 1.  
  
 [ @level0name=] {"*level0_object_name*"}  
 Имя указанного типа объекта уровня 1. *level0_object_name* — **sysname** значение по умолчанию NULL.  
  
 [ @level1type=] {"*level1_object_type*"}  
 Тип объекта уровня 1. *level1_object_type* — **varchar(128)** значение по умолчанию NULL. Допустимые входные данные: AGGREGATE, DEFAULT, FUNCTION, LOGICAL FILE NAME, PROCEDURE, QUEUE, RULE, SYNONYM, TABLE, TABLE_TYPE, TYPE, VIEW, XML SCHEMA COLLECTION и NULL.  
  
 [ @level1name=] {"*level1_object_name*"}  
 Имя указанного типа объекта уровня 1. *level1_object_name* — **sysname** значение по умолчанию NULL.  
  
 [ @level2type=] {"*level2_object_type*"}  
 Тип объекта уровня 2. *level2_object_type* — **varchar(128)** значение по умолчанию NULL. Допустимые входные данные: COLUMN, CONSTRAINT, EVENT NOTIFICATION, INDEX, PARAMETER, TRIGGER и NULL.  
  
 [ @level2name=] {"*level2_object_name*"}  
 Имя указанного типа объекта уровня 2. *level2_object_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 С целью указания расширенных свойств объекты в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распределены по трем уровням (0, 1 и 2). Уровень 0 является высшим уровнем и определяется как «объекты в области базы данных». Объекты уровня 1 содержатся в схеме и в пользовательской области, а объекты уровня 2 содержатся в объектах уровня 1. Расширенные свойства могут быть определены для объектов на любом из этих уровней. Ссылки на объект определенного уровня должны быть уточнены именами объектов более высокого уровня, в которых они содержатся или которым они принадлежат.  
  
 Задан допустимый *property_name* и *значение*, если все типы и имена объектов имеют значение null, то обновляемое свойство принадлежит текущей базе данных.  
  
## <a name="permissions"></a>Разрешения  
 Члены предопределенной роли базы данных db_ddladmin и db_owner могут обновлять расширенные свойства любого объекта со следующим исключением: db_ddladmin не могут добавлять свойства к самой базе данных, пользователям или ролям.  
  
 Пользователи могут обновлять расширенные свойства принадлежащих им объектов, а также свойства, для которых у этих пользователей есть разрешения ALTER или CONTROL.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-updating-an-extended-property-on-a-column"></a>A. Обновление расширенного свойства столбца  
 В следующем примере обновляется значение свойства `Caption` столбца `ID` в таблице `T1`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE T1 (id int , name char (20));  
GO  
EXEC sp_addextendedproperty   
    @name = N'Caption'  
    ,@value = N'Employee ID'  
    ,@level0type = N'Schema', @level0name = dbo  
    ,@level1type = N'Table',  @level1name = T1  
    ,@level2type = N'Column', @level2name = id;  
GO  
--Update the extended property.  
EXEC sp_updateextendedproperty   
    @name = N'Caption'  
    ,@value = 'Employee ID must be unique.'  
    ,@level0type = N'Schema', @level0name = dbo  
    ,@level1type = N'Table',  @level1name = T1  
    ,@level2type = N'Column', @level2name = id;  
GO  
```  
  
### <a name="b-updating-an-extended-property-on-a-database"></a>Б. Обновление расширенного свойства базы данных  
 В следующем примере расширенное свойство образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] создается, затем обновляется.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_addextendedproperty   
@name = N'NewCaption', @value = 'AdventureWorks2012 Sample OLTP Database';  
GO  
USE AdventureWorks2012;  
GO  
EXEC sp_updateextendedproperty   
@name = N'NewCaption', @value = 'AdventureWorks2012 Sample Database';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.fn_listextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sys.extended_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
