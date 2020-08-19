---
description: sys.dm_external_script_execution_stats
title: sys. dm_external_script_execution_stats | Документация Майкрософт
ms.custom: ''
ms.date: 06/25/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_execution_stats
- sys.dm_external_script_execution_stats_TSQL
- dm_external_script_execution_stats
- dm_external_script_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_execution_stats dynamic management view
ms.assetid: 2e99f026-ceb2-42a2-a549-c71d31ed0cf4
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 9c8244de0efc2bdd3dc506e5e1ebcddcd4843dea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489927"
---
# <a name="sysdm_external_script_execution_stats"></a>sys.dm_external_script_execution_stats
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

Возвращает по одной строке для каждого типа запроса внешнего скрипта. Запросы внешних скриптов группируются по поддерживаемому языку внешних скриптов. Одна строка создается для каждой зарегистрированной функции внешних скриптов. Произвольные функции внешних скриптов не регистрируются, пока не будут отправлены родительским процессом, таким как `rxExec`.
  
> [!NOTE]  
> Это динамическое административное представление доступно только в том случае, если вы установили и включили функцию, поддерживающую выполнение внешних скриптов. Дополнительные сведения см. в разделе [r Services in SQL Server 2016](../../machine-learning/r/sql-server-r-services.md), [службы машинного обучения (R, Python) в SQL Server 2017 и более поздних версиях](../../machine-learning/sql-server-machine-learning-services.md) и [Azure управляемый экземпляр службы машинного обучения](/azure/azure-sql/managed-instance/machine-learning-services-overview).
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|язык|**nvarchar**|Имя зарегистрированного языка внешних скриптов. Каждый внешний скрипт должен указывать язык в запросе скрипта, чтобы открыть соответствующее средство запуска. |  
|counter_name|**nvarchar**|Имя зарегистрированной функции внешних скриптов. Не допускает значение NULL.|  
|counter_value|**integer**|Общее количество экземпляров, где вызывалась зарегистрированная функция внешних скриптов на сервере. Данное значение является совокупным (подсчет ведется с момента установки компонента на экземпляре) и не может быть сброшено.|  

## <a name="permissions"></a>Разрешения

 Требуется разрешение VIEW SERVER STATE для сервера.  
  
> [!NOTE]  
> Пользователям, выполняющим внешние скрипты, требуется дополнительное разрешение EXECUTE ANY EXTERNAL SCRIPT, однако администраторы могут использовать это динамическое административное представление без такого разрешения.
  
## <a name="remarks"></a>Комментарии

  Это динамическое административное представление предоставляется для внутренней телеметрии, чтобы отслеживать общее использование новой функции выполнения внешних скриптов в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Служба телеметрии запускается вместе с LaunchPad и увеличивает значение счетчика на диске при каждом вызове зарегистрированной функции внешнего скрипта.

В общем случае счетчики производительности допустимы только при условии, что активен создавший их процесс. Таким образом, запрос к динамическому административному представлению не может отобразить подробные данные для остановленной службы. Например, если средство запуска выполняет внешний сценарий и, но все же завершается очень быстро, обычное динамическое административное представление может не отображать данные.

Поэтому счетчики, отслеживаемые этим динамическим административным представлением, продолжают выполняться, а состояние для sys.dm_external_script_requests сохраняется путем записи на диск, даже при завершении работы экземпляра.

### <a name="counter-values"></a>Значения счетчика

В SQL Server 2016 поддерживается только язык R, а запросы внешних скриптов обрабатываются [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] . В SQL Server 2017 и более поздних версиях и в Управляемый экземпляр SQL Azure поддерживаются и R, и Python, а запросы внешних скриптов обрабатываются [!INCLUDE[rsql_productname_md](../../includes/rsql-productnamenew-md.md)] .

Для R это динамическое административное представление отслеживает количество вызовов R, выполненных в экземпляре. Например, если вызывается `rxLinMod` , который запускается параллельно, счетчик увеличивается на 1.

Для языка R значения счетчиков отображаются в поле *counter_name* , представляя имена зарегистрированных функций ScaleR. Значения в поле *counter_value* представляют совокупное количество экземпляров для определенной функции ScaleR. 

Для Python это динамическое административное представление отслеживает количество вызовов Python, выполненных в экземпляре.

Отсчет начинается при установке и включении компонента на экземпляре и накапливается до тех пор, пока файл с данными о состоянии не будет удален или перезаписан администратором. Таким образом, в общем случае сбросить значения в поле *counter_value*нельзя. Если вы хотите отслеживать использование по сеансу, времени календаря или другим интервалам, рекомендуется перехватывать счетчики с занесением в таблицу.

### <a name="registration-of-external-script-functions-in-r"></a>Регистрация внешних функций скриптов в R

R поддерживает произвольные сценарии, а сообщество R предоставляет множество тысяч пакетов, каждый из которых имеет собственные функции и методы. Однако это динамическое административное представление отслеживает только функции масштабирования, установленные со службами SQL Server 2016 R.

Регистрация этих функций выполняется при установке компонента, а сами зарегистрированные функции нельзя добавлять или удалять.

## <a name="examples"></a>Примеры  
  
### <a name="viewing-the-number-of-r-scripts-run-on-the-server"></a>Просмотр количества скриптов R, запущенных на сервере

 Следующий пример показывает совокупное число выполнений внешних скриптов для языка R.  
  
```sql
SELECT counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE language = 'R';
```  

### <a name="viewing-the-number-of-python-scripts-run-on-the-server"></a>Просмотр числа сценариев Python, выполняемых на сервере

В следующем примере показано общее количество выполнений внешних скриптов для языка Python.  
  
```sql
SELECT counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE language = 'Python';
```  

## <a name="see-also"></a>См. также

+ [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Динамические административные представления и функции, связанные с выполнением (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)
+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
