---
title: "float и real (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: dd20fe12af6f1dcaf378d737961bc2ba354aabe5
ms.openlocfilehash: 0ce2e3272c30057f533796e0822256c6235de0c1
ms.contentlocale: ru-ru
ms.lasthandoff: 10/04/2017

---
# <a name="float-and-real-transact-sql"></a>Типы данных float и real (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Типы приблизительных числовых данных, используемые для числовых данных с плавающей запятой. Данные с плавающей запятой являются приблизительными, поэтому не все значения из диапазона могут быть отображены точно. Синонимом по стандарту ISO для **реальные** — **float(24)**.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
**число с плавающей запятой** [ **(***n***)** ] где  *n*  — количество битов, используемых для хранения мантиссы **float** число в экспоненциальном представлении и определяет размер, точность и хранилища. Если  *n*  указано, оно должно быть значением между **1** и **53**. Значение по умолчанию  *n*  — **53**.
  
|*n*значение|Точность|Объем памяти|  
|---|---|---|
|**1-24**|7 знаков|4 байта|  
|**25-53**|15 знаков|8 байт|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]рассматривает  *n*  как один из двух возможных значений. Если **1**<=n<=**24**,  *n*  рассматривается как **24**. Если **25**<=n<=**53**,  *n*  рассматривается как **53**.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Float**[**(n)**] тип данных соответствует стандарту ISO для всех значений  *n*  из **1** через **53**. Синоним для **двойной точности** — **float(53)**.
  
## <a name="remarks"></a>Замечания  
  
|Тип данных|Диапазон|Память|  
|---|---|---|
|**float**|- 1,79E+308 — -2,23E-308, 0 и 2,23E-308 — 1,79E+308|Зависит от значения*n*|  
|**real**|- 3,40E + 38 — -1,18E - 38, 0 и 1,18E - 38 — 3,40E + 38|4 байта|  
  
##  <a name="converting-float-and-real-data"></a>Преобразование данных float и real  
Значения **float** усекаются, если они преобразуются в любой целочисленный тип.
  
При необходимости преобразования из **float** или **реальные** в символьные данные, используя строковую функцию STR обычно более полезными, чем CAST (). Это объясняется большими возможностями функции STR в отношении форматирования. Дополнительные сведения см. в разделе [СТРУ &#40; Transact-SQL &#41; ](../../t-sql/functions/str-transact-sql.md) и [функции &#40; Transact-SQL &#41; ](../../t-sql/functions/functions.md).
  
Преобразование **float** значения, которые используют экспоненциальный формат для **десятичное** или **числовое** ограничена только 17 знаков точности. Любое значение < 5E-18 округляется до 0.
  
## <a name="see-also"></a>См. также:
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Преобразование типов данных &#40; компонент Database Engine &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  

