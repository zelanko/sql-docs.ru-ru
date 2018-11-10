---
title: decimal и numeric (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c56435e2b0b576ae33ddb00f631fde8dee608ff7
ms.sourcegitcommit: b58d514879f182fac74d9819918188f1688889f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/02/2018
ms.locfileid: "50970458"
---
# <a name="decimal-and-numeric-transact-sql"></a>decimal и numeric (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

> [!div class="nextstepaction"]
> [Помогите улучшить документацию по SQL Server!](https://80s3ignv.optimalworkshop.com/optimalsort/36yyw5kq-0)

Типы числовых данных с фиксированными точностью и масштабом. Типы decimal и numeric являются взаимозаменяемыми синонимами.
  
## <a name="arguments"></a>Аргументы  
**decimal**[ **(***p*[ **,***s*] **)**] и **numeric**[ **(***p*[ **,***s*] **)**]  
Числа с фиксированной точностью и масштабом. При использовании максимальной точности числа могут принимать значения в диапазоне от -10^38+1 до 10^38-1. Синонимами типа **decimal** по стандарту ISO являются типы **dec** и **dec(***p*, *s***)**. Тип **numeric** функционально эквивалентен типу **decimal**.
  
p (точность)  
Максимальное количество десятичных разрядов числа (как слева, так и справа от десятичной запятой), которые будут храниться. Точность должна быть значением в диапазоне от 1 до максимум 38. Точность по умолчанию составляет 18.
  
> [!NOTE]  
>  В Informatica поддерживаются только 16 значащих разрядов независимо от указанных точности и масштаба.  
  
*s* (масштаб)  
Максимальное количество хранимых десятичных разрядов числа справа от десятичной запятой. Это число отнимается от *p* для определения максимального количества цифр слева от десятичной запятой. Масштаб должен иметь значение от 0 до *p*. Масштаб может быть указан только совместно с точностью. По умолчанию масштаб имеет значение 0, поэтому 0 <= *s* \<= *p*. Максимальный размер хранилища зависит от точности.
  
|Точность|Байты хранилища|  
|---|---|
|1–9|5|  
|10–19|9|  
|20–28|13|  
|29–38|17|  
  
> [!NOTE]  
>  В Informatica (при подключении с помощью соединителя SQL Server PDW для Informatica) поддерживаются только 16 значащих разрядов независимо от указанных точности и масштаба.  
  
## <a name="converting-decimal-and-numeric-data"></a>Преобразование данных типов decimal и numeric
Для типов данных **decimal** и **numeric** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обрабатывает каждое конкретное сочетание точности и масштаба как различные типы данных. Например, значения **decimal(5,5)** и **decimal(5,0)** считаются разными типами данных.
  
В инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] константа с десятичным разделителем автоматически преобразуется в значение типа **numeric** с минимальными необходимыми точностью и масштабом. Например, константа 12,345 преобразуется в значение **numeric** с точностью 5 и масштабом 3.
  
Преобразование типа данных **decimal** или **numeric** в тип **float** или **real** может привести к потере точности. Преобразование типов данных **int**, **smallint**, **tinyint**, **float**, **real**, **money** или **smallmoney** в тип **decimal** или **numeric** может вызвать переполнение.
  
По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует округление с потерей точности и масштаба при преобразовании числа в значение **decimal** или **numeric**. Однако при включенном (ON) параметре SET ARITHABORT в случае переполнения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызывает ошибку. Для возникновения ошибки недостаточно только потери точности и масштаба.
  
При преобразовании значений с плавающей запятой или действительных значений в десятичное или числовое, число десятичных разрядов в десятичном значении никогда не превышает 17. Любое значение с плавающей запятой < 5E-18 преобразуется в 0.
  
## <a name="examples"></a>Примеры  
В приведенном ниже примере создается таблица, в которой используются типы данных **decimal** и **numeric**.  Значения вставляются в каждый столбец и результаты возвращаются с помощью инструкции SELECT.
  
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
  
## <a name="see-also"></a>См. также раздел
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[sys.types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  
