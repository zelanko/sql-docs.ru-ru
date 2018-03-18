---
title: "Параметры сортировки | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLATE
- COLLATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], COLLATE clause
- COLLATE clause
ms.assetid: 76763ac8-3e0d-4bbb-aa53-f5e7da021daa
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7a206f638b78a5e4311ab7889a7902aa39a17413
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="collations"></a>Параметры сортировки
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Предложение, которое может применяться к определению базы данных или столбца для определения параметров сортировки, а также к выражению символьной строки, чтобы применить приведение параметров сортировки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
COLLATE { <collation_name> | database_default }  
<collation_name> :: =   
     { Windows_collation_name } | { SQL_collation_name }  
```  
  
## <a name="arguments"></a>Аргументы  
 *collation_name*  
 Имя параметров сортировки, применяемых к выражению, определению столбца или определению базы данных. Аргументом *collation_name* может быть только заданное имя *Windows_collation_name* или *SQL_collation_name*. Аргумент *collation_name* должен быть литеральным значением. Имя *collation_name* не может быть представлено переменной или выражением.  
  
 Аргумент *Windows_collation_name* является именем параметров сортировки для [Windows Collation Name](../../t-sql/statements/windows-collation-name-transact-sql.md).  
  
 Аргумент *SQL_collation_name* является именем параметров сортировки для [SQL Server Collation Name](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 При применении параметров сортировки на уровне определения базы данных параметры сортировки Windows «Только для Юникода» нельзя использовать с предложением COLLATE.  
  
 **database_default**  
 Заставляет предложение COLLATE наследовать параметры сортировки текущей базы данных.  
  
## <a name="remarks"></a>Remarks  
 Предложение COLLATE можно указывать на нескольких уровнях. следующие основные параметры.  
  
1.  Создание или изменение базы данных.  
  
     Предложение COLLATE можно использовать в инструкциях CREATE DATABASE и ALTER DATABASE для указания параметров сортировки по умолчанию для базы данных. Можно также задать параметры сортировки при создании базы данных с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Если не указывать параметры сортировки, базе данных присваиваются параметры сортировки по умолчанию для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Параметры сортировки Windows "Только для Юникода" могут использоваться только с предложением COLLATE для применения параметров сортировки к данным типа **nchar**, **nvarchar** или **ntext** на уровне столбца и уровне выражения. Их нельзя применять с предложением COLLATE для изменения параметров сортировки экземпляра базы данных или сервера.  
  
2.  Создание или изменение столбца таблицы.  
  
     Параметры сортировки можно указать для каждого столбца символьной строки с помощью предложения COLLATE в инструкциях CREATE TABLE и ALTER TABLE. Можно также задать параметры сортировки при создании таблицы с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Если не указывать параметры сортировки, столбцу присваиваются параметры сортировки по умолчанию для базы данных.  
  
     Кроме того, в предложении COLLATE можно использовать параметр `database_default` для указания того, что столбец во временной таблице должен использовать параметры сортировки текущей пользовательской базы данных, заданные по умолчанию для соединения, а не параметры сортировки базы данных **tempdb**.  
  
3.  Приведение параметров сортировки выражения.  
  
     Предложение COLLATE можно использовать для применения символьного выражения к определенным параметрам сортировки. Символьным литералам и переменным присваиваются параметры сортировки по умолчанию для текущей базы данных. Ссылкам столбцов присваивается определение параметров сортировки для столбца.  
  
 Параметры сортировки идентификатора зависят от уровня, для которого определен этот идентификатор. К идентификаторам объектов на уровне экземпляров, таких как имена входа и имена базы данных, применяются параметры сортировки по умолчанию для экземпляра. К идентификаторам объектов внутри базы данных, таких как таблицы, представления и имена столбцов, применяются параметры сортировки, используемые по умолчанию для базы данных. Например: две таблицы, имена которых отличаются только регистром, можно создать в базе данных с параметрами сортировки, учитывающими регистр букв, но нельзя создать в базе данных с параметрами сортировки без учета регистра. Дополнительные сведения см. в разделе [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
 Переменные, метки GOTO, временные хранимые процедуры и временные таблицы можно создавать, если контекст соединения связан с одной базой данных, и ссылка на которую сохраняется, когда контекст переключается на другую базу данных. Идентификаторы переменных, меток GOTO, временных хранимых процедур и временных таблиц имеют параметры сортировки по умолчанию для экземпляра сервера.  
  
 Предложение COLLATE можно применять только к типам данных **char**, **varchar**, **text**, **nchar**, **nvarchar** и **ntext**.  
  
 COLLATE использует аргумент *collate_name* для ссылки на имя параметров сортировки SQL Server или Windows, которые применяются к выражению, определению столбца или определению базы данных. *collation_name* может быть только указанным *Windows_collation_name* или *SQL_collation_name*, и параметр должен содержать литеральное значение. Имя *collation_name* не может быть представлено переменной или выражением.  
  
 Параметры сортировки обычно определяются по имени, за исключением программы установки. В программе установки вместо имени указывается обозначение базовых параметров сортировки (языковой стандарт параметров сортировки) для параметров сортировки Windows, а затем определяются настройки сортировки с учетом или без учета регистра или диакритических знаков.  
  
 Чтобы получить список всех допустимых имен параметров сортировки для Windows и SQL Server, можно выполнить системную функцию [fn_helpcollations](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md):  
  
```sql  
SELECT name, description  
FROM fn_helpcollations();  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает только кодовые страницы, существующие в базовой операционной системе. При выполнении операции, зависящей от параметров сортировки, используемых ссылочным объектом, параметры сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны использовать кодовую страницу, которая поддерживается работающей на компьютере операционной системой. Эти операции могут включать:  
  
-   указание параметров сортировки по умолчанию для базы данных при ее создании или изменении;  
  
-   указание параметров сортировки для столбца при создании или изменении таблицы;  
  
-   при восстановлении или присоединении базы данных параметры сортировки по умолчанию и параметры сортировки всех столбцов типа **char**, **varchar** и **text** или параметров базы данных должны поддерживаться операционной системой.  
  
> [!NOTE]
> Преобразование кодовых страниц поддерживается для типов данных **char** и **varchar**, однако поддержка типа данных **text** не предусмотрена. Сообщения о потере данных во время преобразования кодовых страниц не выводятся.  
  
> [!NOTE]
> Если параметры сортировки, заданные или применяемые объектом, на который указывает ссылка, используют кодовую страницу, не поддерживаемую Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выдает ошибку.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-specifying-collation-during-a-select"></a>A. Указание параметров сортировки во время выбора  
 В следующем примере создается простая таблица, а затем вставляются четыре строки. Затем в примере применяются два параметра сортировки при выборе данных из таблицы, при этом демонстрируется, что `Chiapas` сортируется по-разному.  
  
```sql  
CREATE TABLE Locations  
(Place varchar(15) NOT NULL);  
GO  
INSERT Locations(Place) VALUES ('Chiapas'),('Colima')  
                             , ('Cinco Rios'), ('California');  
GO  
--Apply an typical collation  
SELECT Place FROM Locations  
ORDER BY Place  
COLLATE Latin1_General_CS_AS_KS_WS ASC;  
GO  
-- Apply a Spanish collation  
SELECT Place FROM Locations  
ORDER BY Place  
COLLATE Traditional_Spanish_ci_ai ASC;  
GO  
```  

Ниже приведены результаты первого запроса.  
  
```
Place 
------------- 
California 
Chiapas 
Cinco Rios 
Colima
```  
  
Ниже приведены результаты второго запроса.  
 
```
Place 
------------- 
California 
Cinco Rios 
Colima 
Chiapas
```  
  
### <a name="b-additional-examples"></a>Б. Дополнительные примеры  
 Дополнительные примеры, в которых используется **COLLATE**, приведены в разделе **Ж. Создание базы данных и назначение имени и параметров сортировки** статьи [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md#examples) и в разделе **Ф. Изменение параметров сортировки столбца** статьи [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md#alter_column).  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)    
 [Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)    
 [Очередность параметров сортировки (Transact-SQL)](../../t-sql/statements/collation-precedence-transact-sql.md)     
 [Константы (Transact-SQL)](../../t-sql/data-types/constants-transact-sql.md)     
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)     
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)     
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)     
 [table (Transact-SQL)](../../t-sql/data-types/table-transact-sql.md)     
  
  
