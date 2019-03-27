---
title: sp_addtype (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addtype
- sp_addtype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addtype
ms.assetid: ed72cd8e-5ff7-4084-8458-2d8ed279d817
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ead23c8feb428772fcde5bcdb59f19e1a23b6cd9
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492846"
---
# <a name="spaddtype-transact-sql"></a>sp_addtype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает псевдоним типа данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [CREATE TYPE](../../t-sql/statements/create-type-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addtype [ @typename = ] type,   
    [ @phystype = ] system_data_type   
    [ , [ @nulltype = ] 'null_type' ] ;  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @typename = ] type` — Имя псевдонима типа данных. Псевдоним имена типов данных должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md) и должны быть уникальными в каждой базе данных. *Тип* — **sysname**, не имеет значения по умолчанию.  
  
`[ @phystype = ] system_data_type` Физический, или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указан, тип данных, на котором основан тип данных псевдонима. *system_data_type* — **sysname**, по умолчанию и может принимать одно из следующих значений:  
  
||||  
|-|-|-|  
|**bigint**|**binary(n)**|**bit**|  
|**char(n)**|**datetime**|**decimal**|  
|**float**|**image**|**int**|  
|**money**|**nchar(n)**|**ntext**|  
|**numeric**|**nvarchar(n)**|**real**|  
|**smalldatetime**|**smallint**|**smallmoney**|  
|**sql_variant**|**text**|**tinyint**|  
|**uniqueidentifier**|**varbinary(n)**|**varchar(n)**|  
  
 Кавычки необходимы для всех параметров, в которых содержатся начальные пробелы или знаки пунктуации. Дополнительные сведения о доступных типах данных см. в разделе [типы данных &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).  
  
 *n*  
 Неотрицательное целое число, которое показывает длину выбранного типа данных.  
  
 *P*  
 Неотрицательное целое число, показывающее максимальное количество десятичных разрядов числа (как слева, так и справа от десятичного разделителя). Дополнительные сведения см. в разделе [decimal и numeric (Transact-SQL)](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *s*  
 Неотрицательное целое число, показывающее максимальное количество десятичных разрядов числа (справа от десятичного разделителя), которое не должно превышать точность. Дополнительные сведения см. в разделе [decimal и numeric (Transact-SQL)](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
`[ @nulltype = ] 'null_type'` Указывает способ обработки значений null типом данных псевдонима. *null_type* — **varchar (** 8 **)**, значение по умолчанию NULL и должен быть заключен в одинарные кавычки ('NULL', 'NOT NULL' или 'NONULL'). Если *null_type* не определяется явным образом **sp_addtype**, ему присваивается текущее допустимость значений NULL по умолчанию. Для определения текущего значения параметра возможности по умолчанию иметь значения NULL используйте системную функцию NULLGETANSINULL. Его можно настраивать с помощью инструкции SET или ALTER DATABASE. Возможность иметь значения NULL необходимо задавать в явной форме. Если **@phystype** — **бит**, и **@nulltype** не указан, по умолчанию не NULL.  
  
> [!NOTE]  
>  *Null_type* параметр только определяет допустимость значений NULL по умолчанию для этого типа данных. Если возможность иметь значения NULL явно указывается для типа данных псевдонима при создании таблицы, эта настройка имеет приоритет над возможностью по умолчанию иметь значения NULL. Дополнительные сведения см. в разделе [ALTER TABLE &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-table-transact-sql.md) и [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Имя типа данных псевдонима должно быть уникальным в базе данных, но типы данных псевдонима с различными именами могут иметь одно определение.  
  
 Выполнение **sp_addtype** создает псевдоним типа данных, которое отображается в **sys.types** представления в указанной базе данных каталога. Если псевдоним типа данных должен быть доступен во всех новых пользовательских базах данных, добавьте его в **модели**. После создания типа данных псевдонима его можно использовать в инструкциях CREATE TABLE и ALTER TABLE, а также привязывать значения по умолчанию и правила к нему. Все скалярные типы данных псевдонима, созданные с помощью **sp_addtype** содержатся в **dbo** схемы.  
  
 Типы данных псевдонима наследуют параметры сортировки базы данных по умолчанию. Параметры сортировки столбцов и переменных типов псевдонима определяются в [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE, ALTER TABLE и DECLARE @*local_variable* инструкций. Изменение параметров сортировки по умолчанию базы данных применяется только к новым столбцам и переменным типа и не изменяет параметры сортировки существующих столбцов и переменных.  
  
> [!IMPORTANT]  
>  В целях обратной совместимости **открытый** роли базы данных автоматически предоставляется разрешение REFERENCES для типов данных псевдонима, созданные с помощью **sp_addtype**. Обратите внимание на то, когда типы данных псевдонима создаются с помощью инструкции CREATE TYPE, а не **sp_addtype**, нет разрешение автоматически не предоставляется.  
  
 Псевдонимы типов данных не может быть определен с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp**, **таблицы**, **xml**, **varchar(max)**, **nvarchar(max)** или **varbinary(max)** типов данных.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **db_owner** или **db_ddladmin** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-an-alias-data-type-that-does-not-allow-for-null-values"></a>A. Создание псевдонима типа данных, не поддерживающего значения NULL  
 В следующем примере создается псевдоним типа данных с именем `ssn` (номер социального страхования), основанный на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-предоставленный **varchar** тип данных. Тип данных `ssn` используется для столбцов, хранящих номера карточек социального страхования, состоящих из 11 разрядов (999-99-9999). Эти столбцы не могут иметь значение NULL.  
  
 Обратите внимание на то, что тип `varchar(11)` заключен в одинарные кавычки, поскольку содержит знак пунктуации (скобки).  
  
```  
USE master;  
GO  
EXEC sp_addtype ssn, 'varchar(11)', 'NOT NULL';  
GO  
```  
  
### <a name="b-creating-an-alias-data-type-that-allows-for-null-values"></a>Б. Создание псевдонима типа данных, поддерживающего значения NULL  
 В следующем примере создается тип данных псевдонима (на основе `datetime`) с именем `birthday`, который поддерживает значения NULL.  
  
```  
USE master;  
GO  
EXEC sp_addtype birthday, datetime, 'NULL';  
```  
  
### <a name="c-creating-additional-alias-data-types"></a>В. Создание дополнительных псевдонимов типов данных  
 В следующем примере создается два дополнительных типа данных псевдонима, `telephone` и `fax`, служащих для внутренних и международных номеров телефонов и факсов.  
  
```  
USE master;  
GO  
EXEC sp_addtype telephone, 'varchar(24)', 'NOT NULL';  
GO  
EXEC sp_addtype fax, 'varchar(24)', 'NULL';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [CREATE DEFAULT (Transact-SQL)](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE RULE (Transact-SQL)](../../t-sql/statements/create-rule-transact-sql.md)   
 [sp_bindefault (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_bindrule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_droptype &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)   
 [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [sp_unbindrule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
