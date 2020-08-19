---
description: Обратная косая черта (продолжение строки) (Transact-SQL)
title: Обратная косая черта (продолжение строки) (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/25/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '\_TSQL'
- '\'
dev_langs:
- TSQL
helpviewer_keywords:
- backwhack
- backslash
- escape character
- hack character
- '\ (backslash)'
- backslant
- bash
- reverse slant
- slosh
- reversed virgule
- line continuation character
- reverse solidus
ms.assetid: c97fbb20-3d12-4d0b-9b52-62a229bc83c0
author: rothja
ms.author: jroth
ms.openlocfilehash: 2437daed52cb8b4a79431465f8a27e5464185e23
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459286"
---
# <a name="backslash-line-continuation-transact-sql"></a>Обратная косая черта (продолжение строки) (Transact-SQL)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

`\` разбивает длинную строковую константу, символ или двоичные данные на две или более строк для удобства чтения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 \<first section of string>  
 Начало строки.  
  
 \<continued section of string>  
 Продолжение строки.  
  
## <a name="remarks"></a>Remarks  
Эта команда возвращает первую и последующие секции строки как одну строку без символов обратной косой черты. Новая строка после символа обратной косой черты должна представлять собой символ перевода строки (U+000A) или сочетание символов возврата каретки (U+000D) и перевода строки (U+000A) в указанном порядке. 

## <a name="examples"></a>Примеры  

### <a name="a-splitting-a-character-string"></a>A. Разделение строки символов  

В следующем примере использованы обратная косая черта и возврат каретки для разбиения строки символов на две строчки.  
  
```  
SELECT 'abc\  
def' AS [ColumnResult];  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 abcdef
 ```    

### <a name="b-splitting-a-binary-string"></a>Б. Разделение двоичной строки  

В следующем примере использованы обратная косая черта и возврат каретки для разбиения двоичной строки на две строчки.  

```  
SELECT 0xabc\
def AS [ColumnResult];  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 0xABCDEF
 ```    

## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [(Деление) (Transact-SQL)](../../t-sql/language-elements/divide-transact-sql.md)   
 [(Присваивание деления) (Transact-SQL)](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [Составные операторы (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  
