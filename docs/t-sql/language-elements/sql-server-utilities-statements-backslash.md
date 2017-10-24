---
title: "(Обратная косая черта) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 011025d20b6341b9fa43b25f6c14c91a135a6ffa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-utilities-statements---backslash"></a>Инструкции служебных программ сервера SQL - обратная косая черта
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предоставляет команды, которые не являются [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций, но распознаются **sqlcmd** и **osql** служебных программ и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] редактора кода. Эти команды используются для повышения удобочитаемости и упрощения выполнения пакетов и скриптов.  
  
\ разбивает длинную строку константой на две или несколько строк для удобства чтения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
## <a name="arguments"></a>Аргументы  
 \<Первая секция строки >  
 Начало строки.  
  
 \<Продолжение части строки >  
 Продолжение строки.  
  
## <a name="remarks"></a>Замечания  
 Эта команда возвращает первую и последующие секции строки как одну строку без символов обратной косой черты.  
  
 Обратная косая черта не является инструкцией [!INCLUDE[tsql](../../includes/tsql-md.md)]. Это команда, распознаваемая программами **sqlcmd** и **osql** служебных программ и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] редактора кода.  
  
## <a name="examples"></a>Примеры  
 В следующем примере использованы обратная косая черта и возврат каретки для разбиения строки на две строчки.  
  
```  
SELECT 'abc\  
def' AS ColumnResult;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 abcdef
 ```    
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [&#40; деления &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-transact-sql.md)   
 [&#40; разделить равно &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  

