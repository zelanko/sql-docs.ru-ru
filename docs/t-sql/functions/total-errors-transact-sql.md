---
title: "@@TOTAL_ERRORS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@TOTAL_ERRORS'
- '@@TOTAL_ERRORS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@TOTAL_ERRORS function'
- total errors [SQL Server]
- errors [SQL Server], read/write
- number of disk read/write errors
- disks [SQL Server], errors
- write errors [SQL Server]
- read/write errors
ms.assetid: 09e62428-ee0e-4ef5-b969-da9d255f1199
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 83d639209d35d6516bd9348f40f4eddfd30ddff5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="totalerrors-transact-sql"></a>@@TOTAL_ERRORS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает количество ошибок записи на диске, обнаруженных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с момента последнего запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
@@TOTAL_ERRORS  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **integer**  
  
## <a name="remarks"></a>Замечания  
 Не все ошибки записи, обнаруженные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], учитываются данной функцией. Случайные устранимые ошибки записи исправляются самим сервером и не учитываются. Чтобы отобразить отчет, содержащий ряд [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статистику, включая общее количество ошибок, запустите **sp_monitor**.  
  
## <a name="examples"></a>Примеры  
 В данном примере выдается количество ошибок, обнаруженных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по состоянию на текущий момент времени.  
  
```  
SELECT @@TOTAL_ERRORS AS 'Errors', GETDATE() AS 'As of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Errors      As of                   
----------- ----------------------  
0           3/28/2003 12:32:11 PM   
```  
  
## <a name="see-also"></a>См. также:  
 [sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Системные статистические функции &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
