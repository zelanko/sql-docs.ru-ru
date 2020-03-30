---
title: TRY_CAST (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TRY_CAST_TSQL
- TRY_CAST
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_CAST function
ms.assetid: ea3a16de-995b-415c-b5f0-9355cf7bb401
author: MikeRayMSFT
ms.author: mikeray
monikerRange: = azuresqldb-current||>= sql-server-2016 ||>= sql-server-linux-2017||= sqlallproducts-allversions||>= aps-pdw-2016||= azure-sqldw-latest
ms.openlocfilehash: 915ea023442ab9d787a481cab44259b1fc4a3857
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "70151954"
---
# <a name="try_cast-transact-sql"></a>TRY_CAST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Возвращает значение, приведенное к указанному типу, если приведение проходит успешно; в противном случае возвращает NULL.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TRY_CAST ( expression AS data_type [ ( length ) ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Приводимое значение. Любое допустимое выражение.  
  
 *data_type*  
 Тип данных, к которому следует привести *expression*.  
  
 *length*  
 Необязательное целое число, обозначающее длину целевого типа данных.  
  
 Диапазон допустимых значений определяется значением *data_type*.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает значение, приведенное к указанному типу, если приведение проходит успешно; в противном случае возвращает NULL.  
  
## <a name="remarks"></a>Remarks  
 **TRY_CAST** принимает переданное значение и пытается привести его к указанному типу *data_type*. Если приведение выполнено успешно, то **TRY_CAST** возвращает значение согласно указанному типу *data_type*; если возникла ошибка, возвращается значение NULL. Однако в случае, если будет запрошено явно запрещенное преобразование, функция **TRY_CAST** вернет ошибку.  
  
 **TRY_CAST** не является новым зарезервированным ключевым словом и доступно на любом уровне совместимости. При установлении соединения с удаленными серверами **TRY_CAST** имеет ту же семантику, что и **TRY_CONVERT**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-try_cast-returns-null"></a>A. TRY_CAST возвращает NULL  
 В следующем примере показано, что TRY_CAST возвращает значение NULL, если не удается выполнить приведение.  
  
```sql  
SELECT   
    CASE WHEN TRY_CAST('test' AS float) IS NULL   
    THEN 'Cast failed'  
    ELSE 'Cast succeeded'  
END AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
Cast failed  
  
(1 row(s) affected)  
```  
  
 В следующем примере показано, что выражение должно иметь ожидаемый формат.  
  
```sql  
SET DATEFORMAT dmy;  
SELECT TRY_CAST('12/31/2010' AS datetime2) AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-try_cast-fails-with-an-error"></a>Б. TRY_CAST завершается с ошибкой  
 В следующем примере показано, что TRY_CAST возвращает ошибку, если явное приведение недопустимо.  
  
```sql  
SELECT TRY_CAST(4 AS xml) AS Result;  
GO  
```  
  
 Результатом выполнения этой инструкции будет ошибка, так как целое число не может быть приведено к типу данных XML.  
  
```  
Explicit conversion from data type int to xml is not allowed.  
```  
  
### <a name="c-try_cast-succeeds"></a>В. TRY_CAST выполнено успешно  
 В этом примере показано, что выражение должно иметь ожидаемый формат.  
  
```  
SET DATEFORMAT mdy;  
SELECT TRY_CAST('12/31/2010' AS datetime2) AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------------------  
2010-12-31 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [TRY_CONVERT (Transact-SQL)](../../t-sql/functions/try-convert-transact-sql.md)   
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
