---
title: '@@IDLE (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c17b356a3409128e0fedd9378d82cf0acb7d8781
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894308"
---
# <a name="x40x40idle-transact-sql"></a>&#x40;&#x40;IDLE (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает значение времени простоя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с момента его последнего запуска. Результат указывается в приращениях времени ЦП или «тактах» и является совокупным для всех ЦП, поэтому может превысить фактическое затраченное время. Умножьте его на значение @@TIMETICKS, чтобы преобразовать в микросекунды.  
  
> [!NOTE]  
>  Если время, возвращенное @@CPU_BUSY или @@IO_BUSY, превышает приблизительно 49 дней совокупного времени ЦП, выдается предупреждение об арифметическом переполнении. В этом случае значения переменных @@CPU_BUSY, @@IO_BUSY и @@IDLE являются неточными.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@IDLE  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **integer**  
  
## <a name="remarks"></a>Remarks  
 Чтобы отобразить отчет, содержащий ряд статистических данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните хранимую процедуру **sp_monitor**.  
  
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
 [@@CPU_BUSY (Transact-SQL)](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [sp_monitor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [@@IO_BUSY (Transact-SQL)](../../t-sql/functions/io-busy-transact-sql.md)   
 [Системные статистические функции (Transact-SQL)](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
