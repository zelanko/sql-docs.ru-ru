---
title: Типы данных float и real (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- float
- real_TSQL
- real
- float_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- numeric data type, floating point
- float data type
- floating point data [SQL Server]
- real data type
ms.assetid: 08ea66b7-624e-4d8b-86bc-750ff76cdfc5
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7a9980c471f81b00f4011b449a1dfcaf9a1f5c98
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="float-and-real-transact-sql"></a>Типы данных float и real (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Типы приблизительных числовых данных, используемые для числовых данных с плавающей запятой. Данные с плавающей запятой являются приблизительными, поэтому не все значения из диапазона могут быть отображены точно. Синонимом по стандарту ISO для типа **real** является **float(24)**.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
**float** [ **(***n***)** ] Где *n* — это количество битов, используемых для хранения мантиссы числа в формате **float** при экспоненциальном представлении. Определяет точность данных и размер для хранения. Если указан параметр *n*, это должно быть значение в диапазоне от **1** до **53**. Значение *n* по умолчанию — **53**.
  
|Значение *n*|Точность|Объем памяти|  
|---|---|---|
|**1-24**|7 цифр|4 байта|  
|**25-53**|15 знаков|8 байт|  
  
> [!NOTE]  
>  В приложении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр *n* может принимать одно из двух возможных значений. Если **1**<=n<=**24**, *n* принимает значение **24**. Если **25**<=n<=**53**, *n* принимает значение **53**.  
  
Тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float**[**(n)**] соответствует стандарту ISO для всех значений *n* в диапазоне от **1** до **53**. Синонимом типа **double precision** является тип **float(53)**.
  
## <a name="remarks"></a>Remarks  
  
|Тип данных|Диапазон|Память|  
|---|---|---|
|**float**|- 1,79E+308 — -2,23E-308, 0 и 2,23E-308 — 1,79E+308|Зависит от значения *n*|  
|**real**|- 3,40E + 38 — -1,18E - 38, 0 и 1,18E - 38 — 3,40E + 38|4 байта|  
  
##  <a name="converting-float-and-real-data"></a>Преобразование данных типа float и real  
При преобразовании в любой целочисленный тип данных значения типа **float** усекаются.
  
Если тип данных **float** или **real** нужно преобразовать в символьный тип, то, как правило, строковую функцию STR использовать удобнее, чем CAST( ). Это объясняется большими возможностями функции STR в отношении форматирования. Дополнительные сведения см. в статьях [STR (Transact-SQL)](../../t-sql/functions/str-transact-sql.md) и [Функции (Transact-SQL)](../../t-sql/functions/functions.md).
  
Точность преобразования значений **float**, которые используют экспоненциальное представление, в **decimal** или **numeric** ограничена только 17 знаками. Любое значение меньше 5E-18 округляется до 0.
  
## <a name="see-also"></a>См. также раздел
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Преобразование типов данных (ядро СУБД)](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
