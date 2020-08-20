---
description: sp_table_privileges_ex (Transact-SQL)
title: sp_table_privileges_ex (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_table_privileges_ex
- sp_table_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_table_privileges_ex
ms.assetid: b58d4a07-5c40-4f17-b66e-6d6b17188dda
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2e748ece19ff0d4dadaf966529ed40e0ac9a69be
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492972"
---
# <a name="sp_table_privileges_ex-transact-sql"></a>sp_table_privileges_ex (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @table_server = ] 'table_server'` Имя связанного сервера, для которого возвращаются сведения. Аргумент *table_server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @table_name = ] 'table_name']` Имя таблицы, для которой предоставляются сведения о правах доступа к таблице. Аргумент *table_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_schema = ] 'table_schema'` Схема таблицы. В некоторых средах СУБД является владельцем таблицы. Аргумент *table_schema* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_catalog = ] 'table_catalog'` Имя базы данных, в которой находится указанный *table_name* . Аргумент *table_catalog* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @fUsePattern = ] 'fUsePattern'` Определяет, должны ли символы "_", "%", "[" и "]" интерпретироваться как подстановочные знаки. Допустимые значения: 0 (сопоставление с шаблоном отключено) и 1 (сопоставление с шаблоном включено). *фусепаттерн* имеет **бит**и значение по умолчанию 1.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Имя квалификатора таблицы. Различные продукты СУБД поддерживают имена таблиц (_Квалификаторы_**,** состоящие из трех частей). _владелец_**.** _имя_). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица. Это поле может иметь значение NULL.|  
|**TABLE_SCHEM**|**sysname**|Имя владельца таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя пользователя базы данных, создавшего таблицу. Это поле всегда возвращает значение.|  
|**TABLE_NAME**|**sysname**|Имя таблицы. Это поле всегда возвращает значение.|  
|**GRANTOR**|**sysname**|Имя пользователя базы данных, которому предоставлены разрешения на эту **table_name** в указанный **участник**. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец всегда совпадает с **table_owner**. Это поле всегда возвращает значение. Кроме того, столбец GRANT может быть либо владельцем базы данных (**table_owner**), либо пользователем, которому владелец базы данных предоставил разрешение с помощью предложения WITH GRANT OPTION в инструкции GRANT.|  
|**GRANTEE**|**sysname**|Имя пользователя базы данных, которому были предоставлены разрешения на этот **table_name** указанным объектом **Grant**. Это поле всегда возвращает значение.|  
|**PRIVILEGE**|**varchar (** 32 **)**|Одно из доступных разрешений на таблицу. Разрешения на таблицу могут быть одним из следующих значений или другими значениями, поддерживаемыми источником данных, если определена реализация.<br /><br /> SELECT = **участник** может получать данные для одного или нескольких столбцов.<br /><br /> INSERT = **GRANTEE** может предоставлять данные для новых строк в одном или нескольких столбцах.<br /><br /> UPDATE = **участник** может изменять существующие данные для одного или нескольких столбцов.<br /><br /> DELETE = **получатель** прав может удалять строки из таблицы.<br /><br /> REFERENCEs = **участник** может ссылаться на столбец во внешней таблице в связи "первичный ключ — внешний ключ". В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] связи «первичный-внешний ключ» определяются с помощью ограничений таблицы.<br /><br /> Область действия, предоставленного **участнику** определенным правом доступа к таблице, зависит от источника данных. Например, разрешение UPDATE может позволить **участнику** обновить все столбцы в таблице в одном источнике данных, а только те столбцы, для которых **предоставлено** право на обновление другого источника данных.|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|Указывает, разрешено ли **участнику** предоставлять разрешения другим пользователям. Часто это называется разрешение «grant with grant». Может иметь значение YES, NO или NULL. Неизвестное значение (или NULL) свидетельствует о том, что разрешение «grant with grant» к источнику данных неприменимо.|  
  
## <a name="remarks"></a>Комментарии  
 Возвращаемые результаты упорядочиваются по **TABLE_QUALIFIER**, **table_owner**, **table_name**и **привилегии**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о правах доступа для таблиц с именами, начинающимися на `Product`, в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] из указанного связанного сервера `Seattle1`. ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предполагается, что это связанный сервер).  
  
```  
EXEC sp_table_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Product%',   
   @table_schema = 'Production',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>См. также  
 [sp_column_privileges_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-ex-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры распределенных запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)  
  
  
