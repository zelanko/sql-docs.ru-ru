---
title: Синонимы типов данных (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], synonyms
- alternate names [SQL Server]
- synonyms [SQL Server], data types
ms.assetid: 390eef67-1a49-4185-a971-e07765be9717
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 482177b87fb4d62cbebb64361e0b26ed9a681c1f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47816562"
---
# <a name="data-type-synonyms-transact-sql"></a>Синонимы типов данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Синонимы типов данных включены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ради совместимости со спецификацией ISO. Эти синонимы и соответствующие им системные типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приведены в следующей таблице.
  
|Синоним|Системный тип данных SQL Server|  
|---|---|
|**Binary varying**|**varbinary**|  
|**char varying**|**varchar**|  
|**character**|**char**|  
|**character**|**char(1)**|  
|**character(** *n* **)**|**char(n)**|  
|**character varying(** *n* **)**|**varchar(n)**|  
|**Dec**|**decimal**|  
|**Double precision**|**float**|  
|**float**[**(***n***)**] for *n* = 1-7|**real**|  
|**float**[**(***n***)**] for *n* = 8-15|**float**|  
|**integer**|**int**|  
|**national character(** *n* **)**|**nchar(n)**|  
|**national char(** *n* **)**|**nchar(n)**|  
|**national character varying(** *n* **)**|**nvarchar(n)**|  
|**national char varying(** *n* **)**|**nvarchar(n)**|  
|**national text**|**ntext**|  
|**timestamp**|rowversion|  
  
Синонимы типов данных можно использовать вместо соответствующих базовых типов данных в инструкциях языка определения данных DDL, таких как CREATE TABLE, CREATE PROCEDURE или DECLARE *@variable*. Однако после создания объекта синонимы утрачивают силу. При создании объекта ему назначается базовый тип данных, связанный с синонимом. Никаких признаков того, что в инструкции, создавшей объект, был указан синоним, не остается.
  
Всем объектам, производным от первоначального объекта, таким, как столбцы результирующего набора или выражения, назначается базовый тип данных. Все последующие вызовы функций работы с метаданными, выполняемые для первоначального объекта и любых производных от него объектов, сообщают базовый тип данных, а не синоним. Это имеет место при работе с метаданными, например в процедуре **sp_help** и других системных хранимых процедурах, представлениях информационных схем и различных операциях с метаданными API доступа к данным, сообщающих типы данных столбцов таблицы или результирующего набора.
  
Например, можно создать таблицу, указав тип `national character varying`:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, VarCharCol national character varying(10))  
```  
  
На самом деле столбцу `VarCharCol` при этом будет назначен тип данных **nvarchar(10)**, и все последующие вызовы функций работы с метаданными будут сообщать, что этот столбец имеет тип **nvarchar(10)**, а не **national character varying(10)**.
  
## <a name="see-also"></a>См. также раздел
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
  
  
