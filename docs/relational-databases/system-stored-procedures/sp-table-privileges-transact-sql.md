---
title: sp_table_privileges (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_table_privileges
- sp_table_privileges_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_table_privileges
ms.assetid: 0512e688-4fc0-4557-8dc8-016672c1e3fe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 595f8adb46602109751b1912feed99ae4702fb55
ms.sourcegitcommit: e821cd8e5daf95721caa1e64c2815a4523227aa4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702847"
---
# <a name="sptableprivileges-transact-sql"></a>sp_table_privileges (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает список разрешений (таких как INSERT, DELETE, UPDATE, SELECT, REFERENCES) для указанной таблицы или таблиц.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_table_privileges [ @table_name = ] 'table_name'     
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @table_qualifier = ] 'table_qualifier' ]   
     [ , [ @fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @table_name=] '*table_name*'  
 Таблица, используемая для возврата сведений о каталоге. *table_name* имеет тип **nvarchar (** 384 **)** и не имеет значения по умолчанию. Поиск совпадений по шаблону поддерживается.  
  
 [ @table_owner=] '*table_owner*'  
 Владелец таблицы, используемой для возврата сведений о каталоге. *table_owner*имеет тип **nvarchar (** 384 **)** и значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается. Если владелец не указан, применяются правила видимости таблиц по умолчанию базовой СУБД.  
  
 Если текущий пользователь является владельцем таблицы с указанным именем, возвращаются столбцы этой таблицы. Если *владелец* не указан и текущий пользователь не владеет таблицей с указанным *именем*, эта процедура ищет таблицу с указанной таблицей *table_name* , принадлежащей владельцу базы данных. Если такая таблица существует, возвращаются ее столбцы.  
  
 [ @table_qualifier=] '*table_qualifier*'  
 Имя квалификатора таблицы. *table_qualifier* имеет тип **sysname**и значение по умолчанию NULL. Различные продукты СУБД поддерживают имена таблиц, состоящие из трех частей (*Qualifier.Owner.Name*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица.  
  
 [ @fUsePattern=] '*фусепаттерн*'  
 Определяет, будут ли символы подчеркивания (_), процента (%) и квадратных скобок ([или]) интерпретироваться как подстановочные знаки. Допустимые значения: 0 (сопоставление с шаблоном отключено) и 1 (сопоставление с шаблоном включено). *фусепаттерн* имеет **бит**и значение по умолчанию 1.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|Имя квалификатора таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. Это поле может иметь значение NULL.|  
|TABLE_OWNER|**sysname**|Имя владельца таблицы. Это поле всегда возвращает значение.|  
|TABLE_NAME|**sysname**|Имя таблицы. Это поле всегда возвращает значение.|  
|GRANTOR|**sysname**|Имя пользователя базы данных, предоставившего разрешения на таблицу TABLE_NAME указанному пользователю GRANTEE. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец всегда совпадает с владельцем TABLE_OWNER. Это поле всегда возвращает значение. Столбец GRANTOR может соответствовать или владельцу базы данных (TABLE_OWNER), или пользователю, которому владелец базы данных предоставил разрешение с помощью предложения WITH GRANT OPTION инструкции GRANT.|  
|GRANTEE|**sysname**|Имя пользователя базы данных, которому предоставлены разрешения на таблицу TABLE_NAME указанным пользователем GRANTOR. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]этот столбец всегда включает пользователя базы данных из представления sys. database_principalssystem. Это поле всегда возвращает значение.|  
|PRIVILEGE|**sysname**|Одно из доступных разрешений на таблицу. Разрешения на таблицу могут быть одним из следующих значений (или другими значениями, поддерживаемыми источником данных, если определена реализация).<br /><br /> SELECT = GRANTEE — может получать данные для одного или нескольких столбцов.<br /><br /> INSERT = GRANTEE — может предоставлять данные для новых строк для одного или нескольких столбцов.<br /><br /> UPDATE = GRANTEE — может изменять существующие данные для одного или нескольких столбцов.<br /><br /> DELETE = GRANTEE — может удалять строки из таблицы.<br /><br /> REFERENCES = GRANTEE — может ссылаться на столбец во внешней таблице в связи «первичный-внешний ключ». В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] связи «первичный ключ-внешний ключ» определяются с ограничениями таблицы.<br /><br /> Область действий, предоставляемая пользователю GRANTEE указанным правом доступа к таблице, зависит от источника данных. Например, права доступа UPDATE могут разрешить пользователю GRANTEE обновлять все столбцы таблицы при работе с одним источником данных и только те столбцы, для которых пользователь GRANTOR имеет разрешение UPDATE, при работе с другим источником данных.|  
|IS_GRANTABLE|**sysname**|Указывает, может ли пользователь GRANTEE предоставлять разрешения другим пользователям (так называемые разрешения «право передачи»). Может иметь значение YES, NO или NULL. Неизвестное значение (или NULL) относится к источнику данных, к которому не применимо понятие «право передачи».|  
  
## <a name="remarks"></a>Примечания  
 Хранимая процедура sp_table_privileges эквивалентна функции ODBC SQLTablePrivileges. Возвращенные результаты упорядочиваются по столбцам TABLE_QUALIFIER, TABLE_OWNER, TABLE_NAME и PRIVILEGE.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 Следующий код возвращает сведения о правах доступа, связанных со всеми таблицами, имена которых начинаются на `Contact`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_table_privileges   
   @table_name = 'Contact%';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры &#40;каталога TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
