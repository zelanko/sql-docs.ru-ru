---
title: sys.dm_external_script_execution_stats | Документация Майкрософт
ms.custom: ''
ms.date: 10/28/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
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
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 06b8e29e9aaf02c8e82f541a9113d5943b829b3b
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262160"
---
# <a name="sysdmexternalscriptexecutionstats"></a>sys.dm_external_script_execution_stats
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Возвращает по одной строке для каждого типа запроса внешнего скрипта. Запросы внешних скриптов группируются по поддерживаемому языку внешних скриптов. Одна строка создается для каждой зарегистрированной функции внешних скриптов. Произвольные функции внешних скриптов не регистрируются, пока не будут отправлены родительским процессом, таким как `rxExec`.
  
> [!NOTE]  
> Это динамическое административное представление (DMV) доступна только в том случае, если вы установили и включили функцию, которая поддерживает выполнение внешнего скрипта. Дополнительные сведения см. в разделе [служб R в SQL Server 2016](../../advanced-analytics/r/sql-server-r-services.md) и [служб машинного обучения (R, Python) в SQL Server 2017](../../advanced-analytics/what-is-sql-server-machine-learning.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|language|**nvarchar**|Имя зарегистрированного языка внешних скриптов. Каждый внешний скрипт должен указывать язык в запросе скрипта, чтобы открыть соответствующее средство запуска. |  
|counter_name|**nvarchar**|Имя зарегистрированной функции внешних скриптов. Не допускает значение NULL.|  
|counter_value|**integer**|Общее количество экземпляров, где вызывалась зарегистрированная функция внешних скриптов на сервере. Данное значение является совокупным (подсчет ведется с момента установки компонента на экземпляре) и не может быть сброшено.|  

  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW SERVER STATE для сервера.  
  
> [!NOTE]  
>  Пользователям, выполняющим внешние скрипты, требуется дополнительное разрешение EXECUTE ANY EXTERNAL SCRIPT, однако администраторы могут использовать это динамическое административное представление без такого разрешения. 
  
## <a name="remarks"></a>Примечания  
  Это динамическое административное представление предоставляется для внутренней телеметрии, чтобы отслеживать общее использование новой функции выполнения внешних скриптов в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Служба телеметрии запускается вместе с LaunchPad и увеличивает значение счетчика на диске при каждом вызове зарегистрированной функции внешнего скрипта.

В общем случае счетчики производительности допустимы только при условии, что активен создавший их процесс. Таким образом, запрос к динамическому административному представлению не может отобразить подробные данные для остановленной службы. Например если средство запуска выполняет внешний скрипт и еще очень быстро завершает его, обычной динамическое административное Представление может не отображать все данные.

Поэтому счетчики, отслеживаемые этим динамическим административным представлением, продолжают выполняться, а состояние для sys.dm_external_script_requests сохраняется путем записи на диск, даже при завершении работы экземпляра.

   
  
### <a name="counter-values"></a>Значения счетчика
В SQL Server 2016 поддерживается единственным внешним языком R и обрабатываются запросы внешних скриптов [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. В SQL Server 2017, R и Python, поддерживаемых языков внешних и обрабатываются запросы внешних скриптов с [!INCLUDE[rsql_productname_md](../../includes/rsql-productnamenew-md.md)].

Для R это динамическое административное Представление отслеживает количество вызовов R в экземпляре. Например, если вызывается `rxLinMod` , который запускается параллельно, счетчик увеличивается на 1.
 
Для языка R значения счетчиков отображаются в поле *counter_name* , представляя имена зарегистрированных функций ScaleR. Значения в поле *counter_value* представляют совокупное количество экземпляров для определенной функции ScaleR. 

Для Python это динамическое административное Представление отслеживает количество вызовов Python, выполненных в экземпляре.

Отсчет начинается при установке и включении компонента на экземпляре и накапливается до тех пор, пока файл с данными о состоянии не будет удален или перезаписан администратором. Таким образом, в общем случае сбросить значения в поле *counter_value*нельзя. Если вы хотите отслеживать использование по сеансу, времени календаря или другим интервалам, рекомендуется перехватывать счетчики с занесением в таблицу.

### <a name="registration-of-external-script-functions-in-r"></a>Регистрация функций внешних скриптов на языке R

R поддерживает произвольные скрипты, и сообщество R предлагает многие тысячи пакетов, каждый из которых свои собственные функции и методы. Однако это динамическое административное представление отслеживает только функции ScaleR, установленные вместе со службами R Services SQL Server.

Регистрация этих функций выполняется при установке компонента, а сами зарегистрированные функции нельзя добавлять или удалять.

## <a name="examples"></a>Примеры  
  
### <a name="viewing-the-number-of-r-scripts-run-on-the-server"></a>Просмотр количества скриптов R, запущенных на сервере  
 Следующий пример показывает совокупное число выполнений внешних скриптов для языка R.  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'R';
```  

### <a name="viewing-the-number-of-python-scripts-run-on-the-server"></a>Просмотр количества Python скрипты выполняются на сервере  
 Следующий пример отображает совокупное число выполнений внешних скриптов для языка Python.  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'Python';
```  

  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md) 
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

