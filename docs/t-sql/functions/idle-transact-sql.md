---
title: "@@IDLE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@IDLE_TSQL'
- '@@IDLE'
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], idle
- ticks [SQL Server]
- '@@IDLE function'
- status information [SQL Server], idle time
- idle time [SQL Server]
ms.assetid: 8f49c62a-8da5-4afd-a5eb-4df8ef8be755
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: ab308bcb1fd3ffdda8e901b2238111abaddecb81
ms.contentlocale: ru-ru
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40idle-transact-sql"></a>&#x40;&#x40; IDLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение времени простоя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с момента его последнего запуска. Результат указывается в приращениях времени ЦП или «тактах» и является совокупным для всех ЦП, поэтому может превысить фактическое затраченное время. Умножьте@TIMETICKS преобразовать в микросекунды.  
  
> [!NOTE]  
>  Если время возвращаются в@CPU_BUSY, или @@IO_BUSY превышает приблизительно 49 дней совокупного времени ЦП, появится предупреждение об арифметическом переполнении. В этом случае значение @@CPU_BUSY, @@IO_BUSY и @@IDLE переменные не являются точными.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@IDLE  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **integer**  
  
## <a name="remarks"></a>Замечания  
 Чтобы отобразить отчет, содержащий ряд [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статистики, запустите **sp_monitor**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример показывает возвращение количества миллисекунд простоя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с момента его запуска и до настоящего времени. Для избежания арифметического переполнения при преобразовании значения в микросекунды, в этом примере одно из значений преобразуется в тип данных `float`.  
  
```  
SELECT @@IDLE * CAST(@@TIMETICKS AS float) AS 'Idle microseconds',  
   GETDATE() AS 'as of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
I  
Idle microseconds  as of                   
----------------- ----------------------  
8199934           12/5/2006 10:23:00 AM   
```  
  
## <a name="see-also"></a>См. также:  
 [@@CPU_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)   
 [Системные статистические функции &#40;Transact-SQL&#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  

