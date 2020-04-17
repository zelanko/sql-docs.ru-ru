---
title: sys.dm_external_script_execution_stats Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2019
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
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 9597b55eabb247dc4a95ed83fe04abac5067a269
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488187"
---
# <a name="sysdm_external_script_execution_stats"></a>sys.dm_external_script_execution_stats
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Возвращает по одной строке для каждого типа запроса внешнего скрипта. Запросы внешних скриптов группируются по поддерживаемому языку внешних скриптов. Одна строка создается для каждой зарегистрированной функции внешних скриптов. Произвольные функции внешних скриптов не регистрируются, пока не будут отправлены родительским процессом, таким как `rxExec`.
  
> [!NOTE]  
> Это динамическое представление управления (DMV) доступно только в том случае, если вы установили и включили функцию, поддерживающую выполнение внешнего скрипта. Для получения более подробной информации см. [R-сервисы в S'L Server 2016](../../machine-learning/r/sql-server-r-services.md) и [Службы машинного обучения (R, Python) в S'L Server 2017 и позже.](../../machine-learning/sql-server-machine-learning-services.md)  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Язык|**nvarchar**|Имя зарегистрированного языка внешних скриптов. Каждый внешний скрипт должен указывать язык в запросе скрипта, чтобы открыть соответствующее средство запуска. |  
|counter_name|**nvarchar**|Имя зарегистрированной функции внешних скриптов. Не допускает значение NULL.|  
|counter_value|**integer**|Общее количество экземпляров, где вызывалась зарегистрированная функция внешних скриптов на сервере. Данное значение является совокупным (подсчет ведется с момента установки компонента на экземпляре) и не может быть сброшено.|  

  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW SERVER STATE для сервера.  
  
> [!NOTE]  
>  Пользователям, выполняющим внешние скрипты, требуется дополнительное разрешение EXECUTE ANY EXTERNAL SCRIPT, однако администраторы могут использовать это динамическое административное представление без такого разрешения. 
  
## <a name="remarks"></a>Примечания  
  Это динамическое административное представление предоставляется для внутренней телеметрии, чтобы отслеживать общее использование новой функции выполнения внешних скриптов в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Служба телеметрии запускается вместе с LaunchPad и увеличивает значение счетчика на диске при каждом вызове зарегистрированной функции внешнего скрипта.

В общем случае счетчики производительности допустимы только при условии, что активен создавший их процесс. Таким образом, запрос к динамическому административному представлению не может отобразить подробные данные для остановленной службы. Например, если пусковая установка выполняет внешний скрипт и при этом выполняет его очень быстро, обычный DMV может не отображать данные.

Поэтому счетчики, отслеживаемые этим динамическим административным представлением, продолжают выполняться, а состояние для sys.dm_external_script_requests сохраняется путем записи на диск, даже при завершении работы экземпляра.

   
  
### <a name="counter-values"></a>Встречные ценности
В S'L Server 2016 единственным внешним языком, поддерживаемым [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]R, является R, и внешние запросы скриптов обрабатываются . В s'L Server 2017 как R, так и Python поддерживаются [!INCLUDE[rsql_productname_md](../../includes/rsql-productnamenew-md.md)]внешние языки, а внешние запросы скриптов обрабатываются .

Для R этот DMV отслеживает количество R-вызовов, которые делаются на экземпляре. Например, если вызывается `rxLinMod` , который запускается параллельно, счетчик увеличивается на 1.
 
Для языка R значения счетчиков отображаются в поле *counter_name* , представляя имена зарегистрированных функций ScaleR. Значения в поле *counter_value* представляют совокупное количество экземпляров для определенной функции ScaleR. 

Для Python этот DMV отслеживает количество вызовов Python, которые делаются на экземпляре.

Отсчет начинается при установке и включении компонента на экземпляре и накапливается до тех пор, пока файл с данными о состоянии не будет удален или перезаписан администратором. Таким образом, в общем случае сбросить значения в поле *counter_value*нельзя. Если вы хотите отслеживать использование по сеансу, времени календаря или другим интервалам, рекомендуется перехватывать счетчики с занесением в таблицу.

### <a name="registration-of-external-script-functions-in-r"></a>Регистрация внешних скриптов в R

R поддерживает произвольные сценарии, и сообщество R предоставляет много тысяч пакетов, каждый со своими функциями и методами. Однако это динамическое административное представление отслеживает только функции ScaleR, установленные вместе со службами R Services SQL Server.

Регистрация этих функций выполняется при установке компонента, а сами зарегистрированные функции нельзя добавлять или удалять.

## <a name="examples"></a>Примеры  
  
### <a name="viewing-the-number-of-r-scripts-run-on-the-server"></a>Просмотр количества скриптов R, запущенных на сервере  
 Следующий пример показывает совокупное число выполнений внешних скриптов для языка R.  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'R';
```  

### <a name="viewing-the-number-of-python-scripts-run-on-the-server"></a>Просмотр числа скриптов Python, запущенных на сервере  
 В следующем примере отображается общее количество внешних выполнения скриптов для языка Python.  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'Python';
```  

  
## <a name="see-also"></a>См. также:  
 [Динамические представления и функции управления &#40;&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Выполнение связанных динамического управления Мнения и функции &#40;Transact-S'L&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
 [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

