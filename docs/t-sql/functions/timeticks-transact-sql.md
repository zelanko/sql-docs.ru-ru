---
title: "@@TIMETICKS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@TIMETICKS_TSQL'
- '@@TIMETICKS'
dev_langs:
- TSQL
helpviewer_keywords:
- ticks [SQL Server]
- '@@TIMETICKS function'
- microseconds per tick [SQL Server]
- time [SQL Server], ticks
- number of microseconds per tick
ms.assetid: 9d036633-837f-4309-9c45-3d9600258018
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fb883a5cf2266bfd8fb79273f601c4564e9e8eed
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="timeticks-transact-sql"></a>@@TIMETICKS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает число микросекунд, соответствующих одному такту.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
@@TIMETICKS  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **integer**  
  
## <a name="remarks"></a>Замечания  
 Длительность такта определяется компьютером. Такт операционной системы имеет длительность 31,25 миллисекунды или одну тридцатую секунды.  
  
## <a name="examples"></a>Примеры  
  
```  
SELECT @@TIMETICKS AS 'Time Ticks';  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные статистические функции &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
