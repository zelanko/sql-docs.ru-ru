---
title: STR (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STR
- STR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- converting numbers to characters
- characters [SQL Server], converting
- character data [SQL Server]
- STR function
ms.assetid: de03531b-d9e7-4c3c-9604-14e582ac20c6
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ea01281d77206ceccfe8598efc31d073ceea9391
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "79448264"
---
# <a name="str-transact-sql"></a>STR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает символьные данные, преобразованные из числовых данных. Символьные данные выровнены по правому краю с заданной длиной и десятичной точностью. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STR ( float_expression [ , length [ , decimal ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *float_expression*  
 Выражение приблизительного числового (**float**) типа данных с десятичной запятой.  
  
 *length*  
 Общая длина. Она включает десятичную запятую, знак, цифры и пробелы. Значение по умолчанию равно 10.  
  
 *decimal*  
 Количество знаков справа от десятичной запятой. Значение *decimal* должно быть меньше или равно 16. Если значение *decimal* больше 16, то результат усекается до шестнадцати знаков после запятой.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **varchar**  
  
## <a name="remarks"></a>Remarks  
 Если указано, то значения параметров *length* и *decimal* в функции STR должны быть положительными. Число округляется до целого или по умолчанию, или если десятичный параметр равен 0. Указанная длина должна быть больше или равна части числа до запятой плюс знак числа (если имеется). Короткое выражение *float_expression* выравнивается справа до указанной длины, а длинное *float_expression* усекается до заданного количества цифр после запятой. Например, значением выражения STR(12,10) будет 12. Выравнивается в результирующем наборе вправо. Однако STR(1223, 2) усекает результирующий набор до \*\*. Строковые функции могут быть вложенными.  
  
> [!NOTE]  
>  Чтобы преобразовать данные в кодировку Юникод, используйте функцию STR внутри функций преобразования CONVERT или [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере выражение, состоящее из пяти знаков и десятичной запятой, преобразуется в шестизначную символьную строку. Дробная часть числа округляется до одного десятичного знака.  
  
```  
SELECT STR(123.45, 6, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------  
 123.5  
  
(1 row(s) affected)  
```  
  
 Когда выражение превышает заданную длину, строка возвращает `**` для указанной длины.  
  
```  
SELECT STR(123.45, 2, 2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--  
**  
  
(1 row(s) affected)  
```  
  
 Даже когда в `STR` вложены числовые данные, результатом являются символьные данные с указанным форматом.  
  
```  
SELECT STR (FLOOR (123.45), 8, 3);
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
 123.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
 [FORMAT (Transact-SQL)](../../t-sql/functions/format-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

