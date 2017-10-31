---
title: "Decimal и numeric (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- decimal
- decimal_TSQL
- numeric
- numeric_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- decimal data type
- decimal data type, about decimal data type
- numeric data type
- numeric data type, about numeric data type
ms.assetid: 9d862a90-e6b7-4692-8605-92358dccccdf
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c6c8ec4ea2255e8496b6e5ed464fbff220d270e7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="decimal-and-numeric-transact-sql"></a>decimal и numeric (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Типы числовых данных с фиксированными точностью и масштабом. Decimal и numeric являются синонимами и являются взаимозаменяемыми.
  
## <a name="arguments"></a>Аргументы  
**десятичное число**[ **(***p*[ **,***s*] **)**] и **цифровой** [ **(***p*[ **,***s*] **)**]  
Числа с фиксированной точностью и масштабом. При использовании максимальной точности числа могут принимать значения в диапазоне от -10^38+1 до 10^38-1. Синонимами по стандарту ISO для **десятичное** , **dec** и **dec (***p*, *s***)**. **числовые** функционально эквивалентен **десятичное**.
  
p (точность)  
Максимальное количество десятичных разрядов числа (как слева, так и справа от десятичной запятой), которые будут храниться. Точность должна быть значением в диапазоне от 1 до максимум 38. Точность по умолчанию составляет 18.
  
> [!NOTE]  
>  Informatica поддерживает только 16 значащих цифр, независимо от того, точность и масштаб указано.  
  
*s* (масштаб)  
Максимальное количество хранимых десятичных разрядов числа справа от десятичной запятой. Это значение вычитается из *p* определить максимальное число разрядов слева от десятичной запятой. Максимальное количество десятичных разрядов числа справа от десятичной запятой. Масштаб должен находиться в диапазоне от 0 до *p*. Масштаб может быть указан только совместно с точностью. Масштаб по умолчанию — 0; Таким образом 0 < = *s* \< =  *p*. Максимальный размер хранилища зависит от точности.
  
|Точность|Байты хранилища|  
|---|---|
|1 - 9|5|  
|10-19|9|  
|20-28|13|  
|29-38|17|  
  
> [!NOTE]  
>  Informatica (подключен через соединитель SQL Server PDW информатика) поддерживает только 16 значащих цифр, независимо от того, точность и масштаб указано.  
  
## <a name="converting-decimal-and-numeric-data"></a>Преобразование десятичных и числовых данных.
Для **десятичное** и **числовое** типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] считает, что каждое конкретное сочетание точности и масштаба, как в другой тип данных. Например **decimal(5,5)** и **decimal(5,0)** считаются разными типами данных.
  
В [!INCLUDE[tsql](../../includes/tsql-md.md)] операторы, константы с десятичной точки автоматически преобразуется в **числовое** данных значение, с помощью Минимальная точность и масштабирование необходимости. Например, константа 12,345 преобразуется в **числовое** значение с точностью 5 и масштабом 3.
  
Преобразование из **десятичное** или **числовое** для **float** или **реальные** может привести к некоторой потере точности. Преобразование из **int**, **smallint**, **tinyint**, **float**, **реальные**, **money** , или **smallmoney** либо **десятичное** или **числовое** может привести к переполнению.
  
По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует округления при преобразовании числа в **десятичное** или **числовое** значение с потерей точности и масштаба. Однако при включенном (ON) параметре SET ARITHABORT в случае переполнения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызывает ошибку. Для возникновения ошибки недостаточно только потери точности и масштаба.
  
При преобразовании значений с плавающей запятой или действительных значений в десятичное или числовое, число десятичных разрядов в десятичном значении никогда не превышает 17. Любое значение с плавающей запятой < 5E-18 преобразуется в 0.
  
## <a name="examples"></a>Примеры  
В следующем примере создается таблица, использующая **десятичное** и **числовое** типов данных.  Значения вставляются в каждый столбец и результаты возвращаются с помощью инструкции SELECT.
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyDecimalColumn decimal(5,2)  
,MyNumericColumn numeric(10,5)
  
);  
  
GO  
INSERT INTO dbo.MyTable VALUES (123, 12345.12);  
GO  
SELECT MyDecimalColumn, MyNumericColumn  
FROM dbo.MyTable;  
  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyDecimalColumn                         MyNumericColumn  
--------------------------------------- ---------------------------------------  
123.00                                  12345.12000  
  
(1 row(s) affected)  
  
```  
  
## <a name="see-also"></a>См. также:
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[sys.types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

