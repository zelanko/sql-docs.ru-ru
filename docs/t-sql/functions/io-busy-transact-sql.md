---
title: "@@IO_BUSY (Transact-SQL) | Документы Майкрософт"
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
- '@@IO_BUSY'
- '@@IO_BUSY_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- ticks [SQL Server]
- I/O [SQL Server], time spent performing operations
- '@@IO_BUSY function'
- output operations [SQL Server]
- input operations [SQL Server]
- time [SQL Server], I/O operations
ms.assetid: 3c26770c-41ae-4e34-8c82-7bef920ffbca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d42b1961a8e2c4b6feb43f415f43968fbf68fd8a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40iobusy-transact-sql"></a>&#x40;&#x40;IO_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает время, затраченное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на выполнение операций ввода-вывода с момента последнего запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Результат представляется в интервалах ЦП (тактах) и объединяет информацию обо всех ЦП, поэтому может превышать фактическое время выполнения операций. Умножьте его на значение @@TIMETICKS, чтобы преобразовать в микросекунды.  
  
> [!NOTE]  
>  Если время, возвращенное @@CPU_BUSY или @@IO_BUSY, превышает приблизительно 49 дней совокупного времени ЦП, выдается предупреждение об арифметическом переполнении. В этом случае значения переменных @@CPU_BUSY, @@IO_BUSY и @@IDLE являются неточными.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@IO_BUSY  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **integer**  
  
## <a name="remarks"></a>Remarks  
 Чтобы отобразить отчет, содержащий несколько статистик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните хранимую процедуру sp_monitor.  
  
## <a name="examples"></a>Примеры  
 Следующий код возвращает число миллисекунд, которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потратил на выполнение операций ввода-вывода с момента запуска до текущего момента. Во избежание арифметического переполнения при преобразовании значения в микросекунды в этом примере одно из значений преобразуется в тип данных **float**.  
  
```  
SELECT @@IO_BUSY*@@TIMETICKS AS 'IO microseconds',   
   GETDATE() AS 'as of';  
```  
  
 Типичный результирующий набор:  
  
```  
  
IO microseconds as of                   
--------------- ----------------------  
4552312500      12/5/2006 10:23:00 AM   
```  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_os_sys_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [@@CPU_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [sp_monitor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Системные статистические функции (Transact-SQL)](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
