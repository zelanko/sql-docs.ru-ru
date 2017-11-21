---
title: "бит (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bit_TSQL
- bit
dev_langs:
- TSQL
helpviewer_keywords:
- bit data type
ms.assetid: 40adfd08-a31c-49cb-a172-386bcaa6edee
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3817549e5846c68b422fb941907860896b956d9a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="bit-transact-sql"></a>bit (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Целочисленный тип данных, который может принимать значения 1, 0 или NULL.  
  
## <a name="remarks"></a>Замечания  
[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Оптимизирует хранение **бит** столбцов. Если имеется 8 или меньше **бит** столбцов таблицы, столбцы хранятся как 1 байт. Если имеется от 9 до 16 **бит** столбцы, столбцы хранятся как 2 байта и т.д.
  
Строковые значения TRUE и FALSE можно преобразовать в **бит** значения: TRUE преобразуется в 1, и значение FALSE преобразуется в 0.
  
При преобразовании в битовый тип (bit) любое ненулевое значение приравнивается к 1.
  
## <a name="see-also"></a>См. также:
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Преобразование типов данных &#40; компонент Database Engine &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[sys.types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

