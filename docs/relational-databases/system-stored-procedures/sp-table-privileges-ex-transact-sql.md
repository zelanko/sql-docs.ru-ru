---
title: sp_table_privileges_ex (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_table_privileges_ex
- sp_table_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_table_privileges_ex
ms.assetid: b58d4a07-5c40-4f17-b66e-6d6b17188dda
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2ad7d7746c1bd436a6473d7d25921c7a3437e75a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sptableprivilegesex-transact-sql"></a>sp_table_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает данные о правах доступа для указанной таблицы из указанного связанного сервера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_table_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
     [ , [@fUsePattern =] 'fUsePattern']  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@table_server =** ] **"***table_server***"**  
 Имя связанного сервера, для которого возвращаются данные. *table_server* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@table_name =** ] **"***table_name***"**]  
 Имя таблицы, для которой предоставляются сведения о правах доступа. *имя_таблицы* — **sysname**, значение по умолчанию NULL.  
  
 [  **@table_schema =** ] **"***table_schema***"**  
 Схема таблицы. В некоторых средах СУБД является владельцем таблицы. *table_schema* — **sysname**, значение по умолчанию NULL.  
  
 [  **@table_catalog =** ] **"***значениям table_catalog***"**  
 Имя базы данных, в котором указанный *table_name* находится. *значениям table_catalog* — **sysname**, значение по умолчанию NULL.  
  
 [  **@fUsePattern =**] **"***шаблонов***"**  
 Определяет, следует ли рассматривать символы «_», «%», «[» и «]» как символы-шаблоны. Допустимые значения: 0 (сопоставление с шаблоном отключено) и 1 (сопоставление с шаблоном включено). *Шаблонов* — **бит**, значение по умолчанию 1.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Имя квалификатора таблицы. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*квалификатор ***.*** владелец ***.*** имя*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица. Это поле может иметь значение NULL.|  
|**ПО ЗНАЧЕНИЯМ TABLE_SCHEM**|**sysname**|Имя владельца таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя пользователя базы данных, создавшего таблицу. Это поле всегда возвращает значение.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы. Это поле всегда возвращает значение.|  
|**ОБЪЕКТ, ПРЕДОСТАВЛЯЮЩИЙ РАЗРЕШЕНИЕ**|**sysname**|Имя пользователя базы данных, предоставившего разрешения на таблицу **TABLE_NAME** указанному пользователю **УЧАСТНИК**. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], этот столбец всегда имеет то же, что **TABLE_OWNER**. Это поле всегда возвращает значение. Кроме того, столбец GRANTOR может соответствовать или владельцу базы данных (**TABLE_OWNER**) или пользователь, которому владелец базы данных предоставил разрешение с помощью предложения WITH GRANT OPTION инструкции GRANT.|  
|**УЧАСТНИК**|**sysname**|Имя пользователя базы данных, предоставившего разрешения на таблицу **TABLE_NAME** указанным пользователем **GRANTOR**. Это поле всегда возвращает значение.|  
|**ПРАВО ДОСТУПА**|**varchar (** 32 **)**|Одно из доступных разрешений на таблицу. Разрешения на таблицу могут быть одним из следующих значений или другими значениями, поддерживаемыми источником данных, если определена реализация.<br /><br /> ВЫБЕРИТЕ = **УЧАСТНИКУ** может получать данные для одного или нескольких столбцов.<br /><br /> INSERT = **УЧАСТНИКУ** может предоставлять данные для новых строк для одного или нескольких столбцов.<br /><br /> UPDATE = **УЧАСТНИКУ** может изменять существующие данные для одного или нескольких столбцов.<br /><br /> Удалить = **УЧАСТНИКУ** может удалять строки из таблицы.<br /><br /> REFERENCES = **УЧАСТНИКУ** может ссылаться на столбец во внешней таблице в связи первичного и внешнего ключа. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] связи «первичный-внешний ключ» определяются с помощью ограничений таблицы.<br /><br /> Область действий, предоставляемая пользователю **УЧАСТНИКУ** по конкретной таблицы привилегий — зависит от источника данных. Например, разрешение UPDATE может позволить **УЧАСТНИКУ** для обновления всех столбцов в таблице в одном источнике данных и только те столбцы, для которого **GRANTOR** имеет разрешение UPDATE в другом источнике данных.|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|Указывает, является ли **УЧАСТНИКУ** предоставлять разрешения другим пользователям. Часто это называется разрешение «grant with grant». Может иметь значение YES, NO или NULL. Неизвестное значение (или NULL) свидетельствует о том, что разрешение «grant with grant» к источнику данных неприменимо.|  
  
## <a name="remarks"></a>Замечания  
 Возвращенные результаты сортируются по **TABLE_QUALIFIER**, **TABLE_OWNER**, **TABLE_NAME**, и **прав**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о правах доступа для таблиц с именами, начинающимися на `Product`, в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] из указанного связанного сервера `Seattle1`. ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] считается связанным сервером.)  
  
```  
EXEC sp_table_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Product%',   
   @table_schema = 'Production',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>См. также  
 [sp_column_privileges_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-ex-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Распределенные запросы хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)  
  
  
