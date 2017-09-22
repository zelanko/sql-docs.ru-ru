---
title: "@@IO_BUSY (Transact-SQL) | Документы Microsoft"
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
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 48e1bcd5a80825715ad6aed8649dad843e92c1ea
ms.contentlocale: ru-ru
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40iobusy-transact-sql"></a>& #x 40; & #x 40; IO_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потратил на выполнение операций ввода-вывода с момента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] последнего запуска. Результат представляется в интервалах ЦП (тактах) и объединяет информацию обо всех ЦП, поэтому может превышать фактическое время выполнения операций. Умножьте@TIMETICKS преобразовать в микросекунды.  
  
> [!NOTE]  
>  Если время возвращаются в@CPU_BUSY, или @@IO_BUSY превышает приблизительно 49 дней совокупного времени ЦП, появится предупреждение об арифметическом переполнении. В этом случае значение @@CPU_BUSY, @@IO_BUSY и @@IDLE переменные не являются точными.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@IO_BUSY  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **integer**  
  
## <a name="remarks"></a>Замечания  
 Чтобы отобразить отчет, содержащий несколько статистик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните хранимую процедуру sp_monitor.  
  
## <a name="examples"></a>Примеры  
 Следующий код возвращает число миллисекунд, которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потратил на выполнение операций ввода-вывода с момента запуска до текущего момента. Для избежания арифметического переполнения при преобразовании значения в микросекунды, в примере преобразуется в одно из значений, чтобы **float** тип данных.  
  
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
 [sys.dm_os_sys_info &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [@@CPU_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Системные статистические функции &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  

