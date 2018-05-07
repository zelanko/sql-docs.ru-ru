---
title: sp_fkeys (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fkeys
- sp_fkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fkeys
ms.assetid: 18110444-d38d-4cff-90d2-d1fc6236668b
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fdb582cf8e77e61d7723ea1c6ed2e854ef8f6940
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spfkeys-transact-sql"></a>sp_fkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о логическом внешнем ключе для текущей среды. Эта процедура показывает связь по внешнему ключу, включая отключенные внешние ключи.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_fkeys [ @pktable_name = ] 'pktable_name'   
     [ , [ @pktable_owner = ] 'pktable_owner' ]   
     [ , [ @pktable_qualifier = ] 'pktable_qualifier' ]   
     { , [ @fktable_name = ] 'fktable_name' }   
     [ , [ @fktable_owner = ] 'fktable_owner' ]   
     [ , [ @fktable_qualifier = ] 'fktable_qualifier' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @pktable_name=] '*pktable_name*"  
 Имя таблицы с первичным ключом, применяемое для возврата сведений о каталоге. *pktable_name* — **sysname**, значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Этот параметр или *fktable_name* должен быть указан параметр (или оба).  
  
 [ @pktable_owner=] '*аргумент pktable_owner*"  
 — Это имя владельца таблицы (с первичным ключом), применяемое для возврата сведений о каталоге. *Аргумент pktable_owner* — **sysname**, значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Если *аргумент pktable_owner* не указан, применяются правила видимости таблиц по умолчанию базовой СУБД.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если текущему пользователю принадлежит таблица с указанным именем, возвращаются столбцы этой таблицы. Если *аргумент pktable_owner* не указан и текущий пользователь не является владельцем таблицы с указанным *pktable_name*, то процедура ищет таблицу с указанным *pktable_name* принадлежат владельцу базы данных. Если такая таблица существует, возвращаются ее столбцы.  
  
 [ @pktable_qualifier =] '*pktable_qualifier*"  
 Имя квалификатора таблицы (с первичным ключом). *pktable_qualifier* имеет тип sysname и значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*qualifier.owner.name*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] квалификатор представляет собой имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица.  
  
 [ @fktable_name=] '*fktable_name*"  
 Имя таблицы (с внешним ключом), применяемое для возврата сведений о каталоге. *fktable_name* имеет тип sysname и значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Этот параметр или *pktable_name* должен быть указан параметр (или оба).  
  
 [ @fktable_owner =] '*fktable_owner*"  
 Имя владельца таблицы (с внешним ключом), применяемое для возврата сведений о каталоге. *fktable_owner* — **sysname**, значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Если *fktable_owner* не указан, применяются правила видимости таблиц по умолчанию базовой СУБД.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если текущему пользователю принадлежит таблица с указанным именем, возвращаются столбцы этой таблицы. Если *fktable_owner* не указан и текущий пользователь не является владельцем таблицы с указанным *fktable_name*, то процедура ищет таблицу с указанным *fktable_name* принадлежат владельцу базы данных. Если такая таблица существует, возвращаются ее столбцы.  
  
 [ @fktable_qualifier=] '*fktable_qualifier*"  
 Имя квалификатора таблицы (с внешним ключом). *fktable_qualifier* — **sysname**, значение по умолчанию NULL. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] квалификатор представляет собой имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|PKTABLE_QUALIFIER|**sysname**|Имя квалификатора таблицы (с первичным ключом). Это поле может иметь значение NULL.|  
|PKTABLE_OWNER|**sysname**|Имя владельца таблицы (с первичным ключом). Это поле всегда возвращает значение.|  
|PKTABLE_NAME|**sysname**|Имя таблицы (с первичным ключом). Это поле всегда возвращает значение.|  
|PKCOLUMN_NAME|**sysname**|Имя первичных ключевых столбцов для каждого столбца таблицы TABLE_NAME. Это поле всегда возвращает значение.|  
|FKTABLE_QUALIFIER|**sysname**|Имя квалификатора таблицы (с внешним ключом). Это поле может иметь значение NULL.|  
|FKTABLE_OWNER|**sysname**|Имя владельца таблицы (с внешним ключом). Это поле всегда возвращает значение.|  
|FKTABLE_NAME|**sysname**|Имя таблицы (с внешним ключом). Это поле всегда возвращает значение.|  
|FKCOLUMN_NAME|**sysname**|Имя внешнего ключевого столбца для каждого столбца таблицы TABLE_NAME. Это поле всегда возвращает значение.|  
|KEY_SEQ|**smallint**|Порядковый номер столбца в первичном ключе, состоящем из нескольких столбцов. Это поле всегда возвращает значение.|  
|UPDATE_RULE|**smallint**|Действие, совершаемое над внешним ключом, когда операция SQL является операцией обновления.  Возможные значения:<br /> 0=CASCADE; каскадное изменение в соответствии с внешним ключом.<br /> 1=NO ACTION; отсутствие изменений при наличии внешнего ключа.<br />   2 = задать null <br /> 3 = задать по умолчанию |  
|DELETE_RULE|**smallint**|Действие, совершаемое над внешним ключом, когда операция SQL является операцией удаления. Возможные значения:<br /> 0=CASCADE; каскадное изменение в соответствии с внешним ключом.<br /> 1=NO ACTION; отсутствие изменений при наличии внешнего ключа.<br />   2 = задать null <br /> 3 = задать по умолчанию |  
|FK_NAME|**sysname**|Идентификатор внешнего ключа. Возвращает NULL, если не применим к источнику данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает имя ограничения FOREIGN KEY.|  
|PK_NAME|**sysname**|Идентификатор первичного ключа. Возвращает NULL, если не применим к источнику данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает имя ограничения PRIMARY KEY.|  
  
 Возвращенные результаты упорядочиваются по FKTABLE_QUALIFIER, FKTABLE_OWNER, FKTABLE_NAME и KEY_SEQ.  
  
## <a name="remarks"></a>Замечания  
 Кодирование приложения, в состав которого входят таблицы с отключенными внешними ключами, можно выполнять следующим образом.  
  
-   Временно отключить проверку ограничений (ALTER TABLE NOCHECK или CREATE TABLE NOT FOR REPLICATION) при работе с таблицами, потом включить ее снова.  
  
-   Использовать триггеры кода приложения для принудительного выполнения связей.  
  
Если введено имя таблицы первичных ключей, а имя таблицы внешних ключей — NULL, то процедура sp_fkeys возвращает все таблицы, в которых есть внешний ключ к данной таблице. Если введено имя таблицы внешних ключей, а имя таблицы первичных ключей — NULL, то процедура sp_fkeys возвращает все таблицы, имеющие связь «первичный-внешний ключ» с внешними ключами в таблице внешних ключей.  
  
Хранимая процедура sp_fkeys эквивалентно SQLForeignKeys в ODBC.  
  
## <a name="permissions"></a>Разрешения  
 Требуется `SELECT` на схему.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере выводится список внешних ключей для таблицы `HumanResources.Department` базы данных `AdventureWorks2012`.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_fkeys @pktable_name = N'Department'  
    ,@pktable_owner = N'HumanResources';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В приведенном ниже примере выводится список внешних ключей для таблицы `DimDate` базы данных `AdventureWorksPDW2012`. Строки не возвращаются, поскольку [!INCLUDE[ssDW](../../includes/ssdw-md.md)] не поддерживает внешние ключи.  
  
```sql  
EXEC sp_fkeys @pktable_name = N'DimDate;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры каталога &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_pkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-pkeys-transact-sql.md)  
  
  

