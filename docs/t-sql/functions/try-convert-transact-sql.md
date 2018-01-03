---
title: "TRY_CONVERT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRY_CONVERT_TSQL
- TRY_CONVERT
dev_langs: TSQL
helpviewer_keywords: TRY_CONVERT function
ms.assetid: 3e6e7825-6482-4cb2-a8c2-9abc99e265a6
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5fedc9777146d24cb04fb7652344f244babc8246
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="tryconvert-transact-sql"></a>TRY_CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает значение, приведенное к указанному типу, если приведение проходит успешно; в противном случае возвращает NULL.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TRY_CONVERT ( data_type [ ( length ) ], expression [, style ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *data_type [(длина)]*  
 Тип данных, к которому следует привести *выражение*.  
  
 *expression*  
 Приводимое значение.  
  
 *стиль*  
 Необязательное целочисленное выражение, указывающее, как **TRY_CONVERT** функция является превращение *выражение*.  
  
 *стиль* принимает те же значения, как *стиль* параметр **преобразовать** функции. Дополнительные сведения см. в разделе [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 Диапазон допустимых значений определяется по значению *data_type*. Если *стиль* имеет значение null, то **TRY_CONVERT** возвращает значение null.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает значение, приведенное к указанному типу, если приведение проходит успешно; в противном случае возвращает NULL.  
  
## <a name="remarks"></a>Remarks  
 **TRY_CONVERT** принимает переданное значение и пытается привести его в указанный *data_type*. Если приведение выполнено успешно, **TRY_CONVERT** возвращает значение, что и заданный *data_type*; при возникновении ошибки возвращается значение null. Однако если запрашивается преобразования, которая явно не разрешена, затем **TRY_CONVERT** завершается с ошибкой.  
  
 **TRY_CONVERT** является зарезервированным словом в уровне совместимости 110 и выше.  
  
 Для серверов версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и выше данная функция может быть удаленной. Данная функция не может быть удаленной для серверов с версией ниже [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-tryconvert-returns-null"></a>A. TRY_CONVERT возвращает NULL  
 В следующем примере показано, что TRY_CONVERT возвращает значение NULL, если не удается выполнить приведение.  
  
```sql  
SELECT   
    CASE WHEN TRY_CONVERT(float, 'test') IS NULL   
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
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-tryconvert-fails-with-an-error"></a>Б. TRY_CONVERT возвращает ошибку  
 В следующем примере показано, что TRY_CONVERT возвращает ошибку, если не разрешается явное приведение.  
  
```sql  
SELECT TRY_CONVERT(xml, 4) AS Result;  
GO  
```  
  
 Результатом выполнения этой инструкции будет ошибка, так как целое число не может быть приведено к типу данных XML.  
  
```  
Explicit conversion from data type int to xml is not allowed.  
```  
  
### <a name="c-tryconvert-succeeds"></a>В. TRY_CONVERT выполняется успешно  
 В этом примере показано, что выражение должно иметь ожидаемый формат.  
  
```  
SET DATEFORMAT mdy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
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
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
