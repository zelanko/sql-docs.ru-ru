---
description: bit (Transact-SQL)
title: bit (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- bit_TSQL
- bit
dev_langs:
- TSQL
helpviewer_keywords:
- bit data type
ms.assetid: 40adfd08-a31c-49cb-a172-386bcaa6edee
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4fdedaaf6645980793bb5baf6ebe02344c3d2b7b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422968"
---
# <a name="bit-transact-sql"></a>bit (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Целочисленный тип данных, который может принимать значения 1, 0 или NULL.  
  
## <a name="remarks"></a>Комментарии  
Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] оптимизирует хранение столбцов типа **bit**. Если в таблице имеется 8 или менее столбцов типа **bit**, они хранятся как 1 байт. Если имеется от 9 до 16 столбцов типа **bit**, они хранятся как 2 байта и т. д.
  
Строковые значения TRUE и FALSE можно преобразовать в значения типа **bit**: значение TRUE преобразуется в 1, а значение FALSE преобразуется в 0.
  
При преобразовании в битовый тип (bit) любое ненулевое значение приравнивается к 1.
  
## <a name="see-also"></a>См. также раздел
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Преобразование типов данных (ядро СУБД)](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[sys.types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  
