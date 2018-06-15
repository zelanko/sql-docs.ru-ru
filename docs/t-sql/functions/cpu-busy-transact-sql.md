---
title: '@@CPU_BUSY (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@CPU_BUSY_TSQL'
- '@@CPU_BUSY'
dev_langs:
- TSQL
helpviewer_keywords:
- CPU [SQL Server]
- status information [SQL Server], CPU
- ticks [SQL Server]
- time [SQL Server], CPU activity
- '@@CPU_BUSY function'
- statistical information [SQL Server], CPU
- CPU [SQL Server], activity
ms.assetid: 81ae0e64-79fa-4a74-9aa5-37045c4cd211
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 27eb30bf1a8b176024610affa368a8db1c6607e1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33052801"
---
# <a name="x40x40cpubusy-transact-sql"></a>&#x40;&#x40;CPU_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Эта функция возвращает время, которое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тратит на выполнение активной операции с момента последнего запуска. `@@CPU_BUSY` возвращает результат, измеряемый в приращениях времени ЦП или тактах. Это значение определяется совокупно для всех ЦП, поэтому может превышать действительное истекшее время. Умножьте его на значение [@@TIMETICKS](./timeticks-transact-sql.md), чтобы преобразовать в микросекунды.
  
> [!NOTE]  
>  Если время, возвращенное @@CPU_BUSY или @@IO_BUSY, превышает приблизительно 49 дней совокупного времени ЦП, может появиться предупреждение об арифметическом переполнении. В этом случае значения переменных `@@CPU_BUSY`, `@@IO_BUSY` и `@@IDLE` являются неточными.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```
@@CPU_BUSY  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных
**integer**
  
## <a name="remarks"></a>Remarks  
Чтобы отобразить отчет, содержащий ряд статистических данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая активность ЦП, необходимо выполнить хранимую процедуру [sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md).
  
## <a name="examples"></a>Примеры  
Этот пример возвращает данные об активности ЦП, полученные от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для текущего времени и даты. Пример преобразует одно из значений в тип данных `float`. Это позволяет избежать арифметического переполнения при вычислении значения в микросекундах.
  
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
  
## <a name="see-also"></a>См. также раздел
[sys.dm_os_sys_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)  
[@@IDLE &#40;Transact-SQL&#41;](../../t-sql/functions/idle-transact-sql.md)  
[@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)  
[sp_monitor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)  
[Системные статистические функции (Transact-SQL)](../../t-sql/functions/system-statistical-functions-transact-sql.md)
  
  
