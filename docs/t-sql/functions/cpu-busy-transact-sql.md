---
title: "@@CPU_BUSY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@CPU_BUSY_TSQL'
- '@@CPU_BUSY'
dev_langs: TSQL
helpviewer_keywords:
- CPU [SQL Server]
- status information [SQL Server], CPU
- ticks [SQL Server]
- time [SQL Server], CPU activity
- '@@CPU_BUSY function'
- statistical information [SQL Server], CPU
- CPU [SQL Server], activity
ms.assetid: 81ae0e64-79fa-4a74-9aa5-37045c4cd211
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 337682a73ae351536af64afca77959cbe6297d7f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40cpubusy-transact-sql"></a>&#x40;&#x40;Cpu_busy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Возвращает время, по которому [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функционировал после последнего запуска. Результат приводится в приращениях времени ЦП или тактах, и определяется совокупно для всех процессоров, поэтому может превышать действительное истекшее время. Умножьте@TIMETICKS преобразовать в микросекунды.
  
> [!NOTE]  
>  Если время возвращаются в@CPU_BUSY или @@IO_BUSY превышает приблизительно 49 дней совокупного времени ЦП, появится предупреждение об арифметическом переполнении. В этом случае значение @@CPU_BUSY, @@IO_BUSY и @@IDLE переменные не являются точными.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```
@@CPU_BUSY  
```  
  
## <a name="return-types"></a>Возвращаемые типы
**integer**
  
## <a name="remarks"></a>Замечания  
Чтобы отобразить отчет, содержащий ряд [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статистику, включая загрузку ЦП, запустите [sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md).
  
## <a name="examples"></a>Примеры  
В следующем примере показаны данные об активности ЦП, полученные от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для текущего времени и даты. Для избежания арифметического переполнения при преобразовании значения в микросекунды, в этом примере одно из значений преобразуется в тип данных `float`.
  
```sql
SELECT @@CPU_BUSY * CAST(@@TIMETICKS AS float) AS 'CPU microseconds',   
   GETDATE() AS 'As of' ;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
CPU microseconds As of
---------------- -----------------------
18406250         2006-12-05 17:00:50.600
```
  
## <a name="see-also"></a>См. также:
[sys.dm_os_sys_info &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)  
[@@IDLE &#40;Transact-SQL&#41;](../../t-sql/functions/idle-transact-sql.md)  
[@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)  
[sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)  
[Системные статистические функции &#40;Transact-SQL&#41;#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)
  
  
