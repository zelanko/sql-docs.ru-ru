---
title: "Синонимы (Transact-SQL) типов данных | Документы Microsoft"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], synonyms
- alternate names [SQL Server]
- synonyms [SQL Server], data types
ms.assetid: 390eef67-1a49-4185-a971-e07765be9717
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1d9b1da2bdc7084268740cd7de2580e64ee9698b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="data-type-synonyms-transact-sql"></a>Синонимы типов данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Синонимы типов данных включены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ради совместимости со спецификацией ISO. Эти синонимы и соответствующие им системные типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приведены в следующей таблице.
  
|Синоним|Системный тип данных SQL Server|  
|---|---|
|**Двоичный переменной**|**varbinary**|  
|**переменной типа char**|**varchar**|  
|**символ**|**char**|  
|**символ**|**char(1)**|  
|**символ (**  *n*  **)**|**char(n)**|  
|**символ переменной (**  *n*  **)**|**varchar(n)**|  
|**DEC**|**decimal**|  
|**Число двойной точности**|**float**|  
|**число с плавающей запятой**[**(***n***)**] для  *n*  = 1-7|**real**|  
|**число с плавающей запятой**[**(***n***)**] для  *n*  = 8-15|**float**|  
|**integer**|**int**|  
|**символов национального алфавита (**  *n*  **)**|**nchar(n)**|  
|**Национальный char (**  *n*  **)**|**nchar(n)**|  
|**изменение символов национального алфавита (**  *n*  **)**|**nvarchar(n)**|  
|**Национальный char переменной (**  *n*  **)**|**nvarchar(n)**|  
|**Национальный текста**|**ntext**|  
|**timestamp**|rowversion|  
  
Синонимы типов данных можно использовать вместо имени соответствующего типа базовых данных в инструкции языка DDL описания данных, например CREATE TABLE, CREATE PROCEDURE или DECLARE  *@variable* . Однако после создания объекта синонимы утрачивают силу. При создании объекта ему назначается базовый тип данных, связанный с синонимом. Никаких признаков того, что в инструкции, создавшей объект, был указан синоним, не остается.
  
Всем объектам, производным от первоначального объекта, таким, как столбцы результирующего набора или выражения, назначается базовый тип данных. Все последующие вызовы функций работы с метаданными, выполняемые для первоначального объекта и любых производных от него объектов, сообщают базовый тип данных, а не синоним. Такое поведение характерно операций с метаданными, таких как **sp_help** и другие системные хранимые процедуры, представления информационной схемы или различные операции метаданные API для доступа к данным, сообщающих типы данных таблицы или результирующего набора столбцы.
  
Например, можно создать таблицу, указав тип `national character varying`:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, VarCharCol national character varying(10))  
```  
  
`VarCharCol`фактически назначается **nvarchar(10)** тип данных, и все последующие метаданных функции сообщит о столбце в виде **nvarchar(10)** столбца. Функции метаданных никогда не будет сообщать о них как **varying(10) символов национального алфавита** столбца.
  
## <a name="see-also"></a>См. также:
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
  
  

