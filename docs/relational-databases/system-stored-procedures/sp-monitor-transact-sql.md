---
title: "sp_monitor (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_monitor_TSQL
- sp_monitor
dev_langs: TSQL
helpviewer_keywords: sp_monitor
ms.assetid: cb628496-2f9b-40e4-b018-d0831c4cb018
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b4ef90280e72a7afd6a8787b053115a4bffa4fa
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spmonitor-transact-sql"></a>Хранимая процедура sp_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает статистику о [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_monitor  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Description|  
|-----------------|-----------------|  
|**last_run**|Время **sp_monitor** последнего запуска.|  
|**current_run**|Время **sp_monitor** запущена.|  
|**секунд**|Число секунд, прошедших с момента **sp_monitor** была запущена.|  
|**CPU_BUSY**|Время в секундах, которое ЦП сервера затратил на работу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**IO_BUSY**|Время в секундах, которое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] затратил на операции ввода и вывода.|  
|**время простоя**|Время простоя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в секундах.|  
|**packets_received**|Количество входящих пакетов, считанных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**packets_sent**|Число исходящих пакетов, записанных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**packet_errors**|Количество ошибок, с которыми столкнулся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время чтения и записи пакетов.|  
|**total_read**|Число операций чтения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**total_write**|Число операций записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**total_errors**|Количество ошибок, с которыми столкнулся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время чтения и записи.|  
|**подключения**|Количество входов или попыток входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью набора функций отслеживает объем проделанной работы. Выполнение **sp_monitor** отображает текущие значения, возвращенные этими функциями и показывает, насколько они изменились со времени последнего запуска этой процедуры.  
  
 Для каждого столбца, статистика выводится в виде *номер*(*номер*)-*номер*% или *номер*(*номер*). Первый *номер* определяет количество секунд (для **cpu_busy**, **io_busy**, и **простоя**) или общее количество (для других переменные) с момента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была перезапущена. *Номер* в скобках отображает количество секунд или общее количество с момента последнего **sp_monitor** была запущена. Процент — это доля времени с момента **sp_monitor** последнего запуска. Например, если в отчете отображается **cpu_busy** равно 4250 (215)-68%, ЦП был загружен 4250 секунд со времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вверх, 215 секунд с момента последнего запуска **sp_monitor** был последнего выполнения и 68 процентов Общее время с момента **sp_monitor** последнего запуска.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 Следующий пример выводит сведения о загруженности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
USE master  
EXEC sp_monitor  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
||||  
|-|-|-|  
|**last_run**|**current_run**|**секунд**|  
|29 марта 1998 11:55|4 апреля 1998 14:22|561|  
  
||||  
|-|-|-|  
|**CPU_BUSY**|**IO_BUSY**|**время простоя**|  
|190(0)-0%|187(0)-0%|148(556)-99%|  
  
||||  
|-|-|-|  
|**packets_received**|**packets_sent**|**packet_errors**|  
|16(1)|20(2)|0(0)|  
  
|||||  
|-|-|-|-|  
|**total_read**|**total_write**|**total_errors**|**подключения**|  
|141(0)|54920(127)|0(0)|4(0)|  
  
## <a name="see-also"></a>См. также:  
 [sp_who &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
