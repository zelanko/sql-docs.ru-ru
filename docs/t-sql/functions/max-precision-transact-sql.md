---
title: "@@MAX_PRECISION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@MAX_PRECISION_TSQL'
- '@@MAX_PRECISION'
dev_langs:
- TSQL
helpviewer_keywords:
- precision [SQL Server], @@MAX_PRECISION
- numeric data type, precision level
- decimal data type, precision level
- '@@MAX_PRECISION function'
- data types [SQL Server], precision
ms.assetid: 9e7158a1-e503-422a-b326-3c9b06e181b2
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 530dc9cd780d9dae2df1c326fcd1cc070450290a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40maxprecision-transact-sql"></a>& #x 40; & #x 40; MAX_PRECISION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает уровень точности, используемый **десятичное** и **числовое** типов данных в данный момент установленный на сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
@@MAX_PRECISION  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **tinyint**  
  
## <a name="remarks"></a>Замечания  
 По умолчанию максимальный уровень точности имеет значение 38.  
  
## <a name="examples"></a>Примеры  
  
```  
SELECT @@MAX_PRECISION AS 'Max Precision'  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Decimal и numeric &#40; Transact-SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [Точность, масштаб и длина &#40; Transact-SQL &#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)  
  
  

