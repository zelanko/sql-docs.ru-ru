---
title: Обратная косая черта (продолжение строки) (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- '\_TSQL'
- '\'
dev_langs:
- TSQL
helpviewer_keywords:
- backwhack
- backslash
- excape character
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
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ac938625fdb67188e650a01ebc17a27b33fd9364
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33062051"
---
# <a name="backslash-line-continuation-transact-sql"></a>Обратная косая черта (продолжение строки) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

`\` разбивает длинную строковую константу, символ или двоичные данные на две или более строк для удобства чтения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
## <a name="arguments"></a>Аргументы  
 \<first section of string>  
 Начало строки.  
  
 \<continued section of string>  
 Продолжение строки.  
  
## <a name="remarks"></a>Примечания  
 Эта команда возвращает первую и последующие секции строки как одну строку без символов обратной косой черты.  

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

## <a name="see-also"></a>См. также  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [(Деление) (Transact-SQL)](../../t-sql/language-elements/divide-transact-sql.md)   
 [(Присваивание деления) (Transact-SQL)](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [Составные операторы (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  
