---
title: "sys.dm_external_script_execution_stats | Документы Microsoft"
ms.custom: 
ms.date: 09/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8306c682ddf8e376e13629cc6fe13472e08f59b0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexternalscriptexecutionstats"></a>sys.dm_external_script_execution_stats
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


  Возвращает по одной строке для каждого типа запроса внешнего скрипта. Запросы внешних скриптов группируются по поддерживаемому языку внешних скриптов. Одна строка создается для каждой зарегистрированной функции внешних скриптов. Произвольные функции внешних скриптов не регистрируются, пока не будут отправлены родительским процессом, таким как `rxExec`.

 
  
> [!NOTE]  
>  Это динамическое административное представление доступно только в том случае, если вы установили и включили функцию, которая поддерживает выполнение внешнего скрипта. Сведения о том, как сделать это для скриптов R, см. в разделе [Установка служб SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|language|**nvarchar**|Имя зарегистрированного языка внешних скриптов. Каждый внешний скрипт должен указывать язык в запросе скрипта, чтобы открыть соответствующее средство запуска. |  
|counter_name|**nvarchar**|Имя зарегистрированной функции внешних скриптов. Не допускает значение NULL.|  
|counter_value|**integer**|Общее количество экземпляров, где вызывалась зарегистрированная функция внешних скриптов на сервере. Данное значение является совокупным (подсчет ведется с момента установки компонента на экземпляре) и не может быть сброшено.|  

  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW SERVER STATE для сервера.  
  
> [!NOTE]  
>  Пользователям, выполняющим внешние скрипты, требуется дополнительное разрешение EXECUTE ANY EXTERNAL SCRIPT, однако администраторы могут использовать это динамическое административное представление без такого разрешения. 
  
## <a name="remarks"></a>Remarks  
  Это динамическое административное представление предоставляется для внутренней телеметрии, чтобы отслеживать общее использование новой функции выполнения внешних скриптов в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Служба телеметрии запускается вместе с LaunchPad и увеличивает значение счетчика на диске при каждом вызове зарегистрированной функции внешнего скрипта.

В общем случае счетчики производительности допустимы только при условии, что активен создавший их процесс. Таким образом, запрос к динамическому административному представлению не может отобразить подробные данные для остановленной службы. Например, если средство запуска выполняет внешний скрипт, однако очень быстро завершает его, обычное динамическое административное представление может показывать не все данные

Поэтому счетчики, отслеживаемые этим динамическим административным представлением, продолжают выполняться, а состояние для sys.dm_external_script_requests сохраняется путем записи на диск, даже при завершении работы экземпляра.

   
  
### <a name="r-counter-values"></a>Значения счетчиков R
 Сейчас в [!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)] поддерживается только один язык внешних скриптов — R. Запросы внешних скриптов для языка R обрабатываются [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. 

Для R это динамическое административное Представление отслеживает количество вызовов R в экземпляре. Например, если вызывается `rxLinMod` , который запускается параллельно, счетчик увеличивается на 1.
 
Для языка R значения счетчиков отображаются в поле *counter_name* , представляя имена зарегистрированных функций ScaleR. Значения в поле *counter_value* представляют совокупное количество экземпляров для определенной функции ScaleR. 

Отсчет начинается при установке и включении компонента на экземпляре и накапливается до тех пор, пока файл с данными о состоянии не будет удален или перезаписан администратором. Таким образом, в общем случае сбросить значения в поле *counter_value*нельзя. Если вы хотите отслеживать использование по сеансу, времени календаря или другим интервалам, рекомендуется перехватывать счетчики с занесением в таблицу.

### <a name="registration-of-external-script-functions"></a>Регистрация функций внешних скриптов

Язык R поддерживает произвольные скрипты, и сообщество R предлагает многие тысячи пакетов, каждый из которых имеет свои собственные функции и методы. Однако это динамическое административное представление отслеживает только функции ScaleR, установленные вместе со службами R Services SQL Server.

Регистрация этих функций выполняется при установке компонента, а сами зарегистрированные функции нельзя добавлять или удалять.

## <a name="examples"></a>Примеры  
  
### <a name="viewing-the-number-of-r-scripts-run-on-the-server"></a>Просмотр количества скриптов R, запущенных на сервере  
 Следующий пример показывает совокупное число выполнений внешних скриптов для языка R.  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'R';
```  

  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md) 
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

