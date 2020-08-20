---
description: Синонимы типов данных (Transact-SQL)
title: Синонимы типов данных (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/23/2017
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
ms.openlocfilehash: f689cdae7253c43ca39c06dc09953c4db02d0def
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88479948"
---
# <a name="data-type-synonyms-transact-sql"></a>Синонимы типов данных (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Синонимы типов данных включены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ради совместимости со спецификацией ISO. Эти синонимы и соответствующие им системные типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приведены в следующей таблице.
  
|Синоним|Системный тип данных SQL Server|  
|---|---|
|**Binary varying**|**varbinary**|  
|**char varying**|**varchar**|  
|**character**|**char**|  
|**character**|**char(1)**|  
|**character(**_n_**)**|**char(n)**|  
|**character varying(**_n_**)**|**varchar(n)**|  
|**Dec**|**decimal**|  
|**Double precision**|**float**|  
|**float**[ **(** _n_ **)** ] for _n_ = 1-7|**real**|  
|**float**[ **(** _n_ **)** ] for _n_ = 8-15|**float**|  
|**integer**|**int**|  
|**national character(**_n_**)**|**nchar(n)**|  
|**national char(**_n_**)**|**nchar(n)**|  
|**national character varying(**_n_**)**|**nvarchar(n)**|  
|**national char varying(**_n_**)**|**nvarchar(n)**|  
|**national text**|**ntext**|  
|**timestamp**|rowversion|  
  
Синонимы типов данных можно использовать вместо соответствующих базовых типов данных в инструкциях языка описания данных DDL. К таким инструкциям относятся CREATE TABLE, CREATE PROCEDURE и DECLARE *\@переменная*. Однако после создания объекта синонимы утрачивают силу. При создании объекта ему назначается базовый тип данных, связанный с синонимом. Никаких признаков того, что в инструкции, создавшей объект, был указан синоним, не остается.
  
Объектам, производным от исходного объекта, таким как столбцы результирующего набора или выражения, назначается базовый тип данных. Все функции метаданных, которые используют исходный объект и любые производные от него объекты, сообщают базовый тип данных, а не синоним, включая:

* операции с метаданными, такие как **sp_help** и другие системные хранимые процедуры,
* представления информационной схемы и
* операции с метаданными API доступа к данным, сообщающих типы данных таблицы или столбцы результирующего набора.
  
Например, можно создать таблицу, указав тип `national character varying`:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, VarCharCol national character varying(10))  
```  
  
Столбцу `VarCharCol` назначен тип данных **nvarchar(10)**, и все следующие вызовы функций работы с метаданными будут сообщать, что этот столбец имеет тип **nvarchar(10)**. а не **national character varying(10)**.
  
## <a name="see-also"></a>См. также
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
  
  
