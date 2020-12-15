---
description: sp_pkeys (Transact-SQL)
title: sp_pkeys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_pkeys
- sp_pkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_pkeys
ms.assetid: e614c75d-847b-4726-8f6f-cd18de688eda
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6a55bcdd0df9f288daa22c5f4f1454b14305ec6a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97478945"
---
# <a name="sp_pkeys-transact-sql"></a>sp_pkeys (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Возвращает сведения о первичном ключе заданной таблицы в текущей среде.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql  
-- Syntax for SQL Server, Azure SQL Database, Azure Synapse Analytics, Parallel Data Warehouse  
  
sp_pkeys [ @table_name = ] 'name'       
    [ , [ @table_owner = ] 'owner' ]   
    [ , [ @table_qualifier = ] 'qualifier' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @table_name =] "*имя*"  
 Таблица, для которой возвращаются сведения. Аргумент *Name* имеет тип **sysname** и не имеет значения по умолчанию. Сопоставление по шаблону не поддерживается.  
  
 [ @table_owner =] "*владелец*"  
 Задает владельца указанной таблицы. Аргумент *owner* имеет тип **sysname** и значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Если параметр *owner* не указан, применяются правила видимости таблиц по умолчанию базовой СУБД.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если текущий пользователь является владельцем таблицы с указанным именем, возвращаются ее столбцы. Если *владелец* не указан и текущий пользователь не владеет таблицей с указанным *именем*, эта процедура ищет таблицу с указанным *именем* , принадлежащую владельцу базы данных. Если такая таблица существует, возвращаются ее столбцы.  
  
 [ @table_qualifier =] "*квалификатор*"  
 Квалификатор таблицы. *квалификатор* имеет тип **sysname** и значение по умолчанию NULL. Различные продукты СУБД поддерживают имена таблиц (_Квалификаторы_**,** состоящие из трех частей). _владелец_**.** _имя_). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, в которой находится таблица.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|Имя квалификатора таблицы. Это поле может иметь значение NULL.|  
|TABLE_OWNER|**sysname**|Имя владельца таблицы. Это поле всегда возвращает значение.|  
|TABLE_NAME|**sysname**|Имя таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя таблицы, отображаемое в таблице sysobjects. Это поле всегда возвращает значение.|  
|COLUMN_NAME|**sysname**|Возвращаются имена всех столбцов в таблице TABLE_NAME. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя столбца, отображаемое в таблице sys.columns. Это поле всегда возвращает значение.|  
|KEY_SEQ|**smallint**|Порядковый номер столбца в первичном ключе, состоящем из нескольких столбцов.|  
|PK_NAME|**sysname**|Идентификатор первичного ключа. Возвращает NULL, если не применим к источнику данных.|  
  
## <a name="remarks"></a>Комментарии  
 Процедура sp_pkeys возвращает сведения о столбцах, явно указанных в ограничении ПЕРВИЧНЫЙ КЛЮЧ. Поскольку не все системы поддерживают явно именованные первичные ключи, разработчик шлюза определяет, что представляет собой первичный ключ. Обратите внимание на то, что под первичным ключом понимается логический первичный ключ таблицы. Предполагается, что для каждого логического первичного ключа определен уникальный индекс. Этот уникальный индекс возвращает хранимая процедура sp_statistics.  
  
 В ODBC аналогом хранимой процедуры sp_pkeys является SQLPrimaryKeys. Результаты упорядочиваются по столбцам TABLE_QUALIFIER, TABLE_OWNER, TABLE_NAME и KEY_SEQ.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается первичный ключ таблицы `HumanResources.Department` в базе данных `AdventureWorks2012`.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_pkeys @table_name = N'Department'  
    ,@table_owner = N'HumanResources';  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере возвращается первичный ключ таблицы `DimAccount` в базе данных `AdventureWorksPDW2012`. Он возвращает нулевые строки, указывающие, что таблица не имеет первичного ключа.  
  
```sql  
-- Uses AdventureWorks  
  
EXEC sp_pkeys @table_name = N'DimAccount';  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры каталога &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

