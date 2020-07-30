---
title: sp_monitor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_monitor_TSQL
- sp_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_monitor
ms.assetid: cb628496-2f9b-40e4-b018-d0831c4cb018
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 400d6f484ee80d9b4b1244aad6b91c8836aa95d4
ms.sourcegitcommit: 08f331b6a5fe72d68ef1b2eccc5d16cb80c6ee39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86977723"
---
# <a name="sp_monitor-transact-sql"></a>Хранимая процедура sp_monitor (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает статистику о [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_monitor  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**last_run**|Время последнего запуска **sp_monitor** .|  
|**current_run**|Время выполнения **sp_monitor** .|  
|**несколько**|Число секунд, прошедших с момента запуска **sp_monitor** .|  
|**cpu_busy**|Время в секундах, которое ЦП сервера затратил на работу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**io_busy**|Время в секундах, которое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] затратил на операции ввода и вывода.|  
|**выключен**|Время простоя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в секундах.|  
|**packets_received**|Количество входящих пакетов, считанных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**packets_sent**|Число исходящих пакетов, записанных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**packet_errors**|Количество ошибок, с которыми столкнулся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время чтения и записи пакетов.|  
|**total_read**|Число операций чтения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**total_write**|Число операций записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**total_errors**|Количество ошибок, с которыми столкнулся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время чтения и записи.|  
|**соединение**|Количество входов или попыток входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью набора функций отслеживает объем проделанной работы. При выполнении **sp_monitor** отображаются текущие значения, возвращаемые этими функциями, и показывается, насколько они изменились с момента последнего выполнения процедуры.  
  
 Для каждого столбца Статистика распечатывается в форме *номер*(*номер*) —*номер*% или *номер*(*число*). Первое *число* обозначает количество секунд (для **CPU_BUSY**, **io_busy**и **бездействие**) или общее число (для других переменных) с момента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапуска. *Число* в круглых скобках обозначает количество секунд или общее число с момента последнего выполнения **sp_monitor** . Процентное значение — это процент времени, прошедших с момента последнего запуска **sp_monitor** . Например, если в отчете отображается **CPU_BUSY** как 4250 (215) — 68%, цп занят 4250 секунд с момента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] последнего запуска, 215 секунды с момента последнего запуска **sp_monitor** и 68 процента от общего времени с момента **sp_monitor** последнего запуска.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 Следующий пример выводит сведения о загруженности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```console
USE master  
EXEC sp_monitor  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

```console
last_run       current_run                   seconds
-----------    --------------------------    ---------
Mar 29 1998    11:55AM Apr 4 1998 2:22 PM    561

cpu_busy           io_busy     idle
---------------    ---------   --------------
190(0)-0%          187(0)-0%   148(556)-99%

packets_received       packets_sent    packet_errors
----------------       ------------    -------------
16(1)                  20(2)           0(0)

total_read     total_write   total_errors    connections
-----------    -----------   -------------   -----------
141(0)         54920(127)    0(0)            4(0)
```
  
## <a name="see-also"></a>См. также:  
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
