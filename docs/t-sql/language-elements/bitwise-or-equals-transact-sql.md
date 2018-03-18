---
title: "|= (побитовое присваивание ИЛИ) (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '|='
- '|=_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, |=
- assignment operators, |=
- augmented operators, |=
- '|= (bitwise OR equals)'
ms.assetid: bd746a4f-6498-4196-bf2e-b6f457a15d44
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 51157a82824e9445860a8cf8d3b6d49de1781b6d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="-bitwise-or-assignment-transact-sql"></a>|= (побитовое присваивание ИЛИ) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Выполняет операцию побитового логического ИЛИ с двумя указанными целочисленными значениями как с преобразованными в двоичные выражения в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] и присваивает значению результат этой операции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression |= expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое выражение [expression](../../t-sql/language-elements/expressions-transact-sql.md) одного из типов данных числовой категории, кроме типа данных **bit**.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает результат типа данных аргумента с более высоким приоритетом. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения см. в статье [&#124; (побитовая операция ИЛИ) (Transact-SQL)](../../t-sql/language-elements/bitwise-or-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Составные операторы (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [Побитовые операторы (Transact-SQL)](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
