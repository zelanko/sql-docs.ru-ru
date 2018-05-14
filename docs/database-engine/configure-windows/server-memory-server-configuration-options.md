---
title: Параметры конфигурации сервера "Server Memory" | Документы Майкрософт
ms.custom: ''
ms.date: 11/27/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Virtual Memory Manager
- max server memory option
- virtual memory [SQL Server]
- VMM
- server memory options [SQL Server]
- servers [SQL Server], memory
- buffer pools [SQL Server]
- min server memory option
- manual memory options [SQL Server]
- memory [SQL Server], servers
ms.assetid: 29ce373e-18f8-46ff-aea6-15bbb10fb9c2
caps.latest.revision: 78
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3544a4530c1650d02952c750d82bb9d51e2d6d50
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="server-memory-server-configuration-options"></a>Параметры конфигурации сервера «Server Memory»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Два параметра памяти сервера, **min server memory** и **max server memory**, используются для изменения в конфигурации объема памяти (в мегабайтах), управляемой диспетчером памяти SQL Server для процесса SQL Server, применяемого экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
По умолчанию параметр **Мин. памяти сервера** имеет значение 0, а параметр **Макс. памяти сервера** — 2 147 483 647 MБ. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может динамически изменять требования к памяти в зависимости от доступных системных ресурсов. Дополнительные сведения см. в разделе [Управление динамической памятью](../../relational-databases/memory-management-architecture-guide.md#dynamic-memory-management). 

Минимальный объем памяти для **max server memory** составляет 128 МБ.
  
> [!IMPORTANT]  
> Если вы зададите слишком высокое значение **Макс. памяти сервера**, одному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], возможно, придется конкурировать с другими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], размещенными на том же узле, за память. Если же задать слишком низкое значение, может возникнуть значительный дефицит памяти или проблемы с производительностью. Если присвоить параметру **Макс. памяти сервера** минимальное значение, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может не запуститься. Если не удается запустить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после изменения этого параметра, запустите его с использованием параметра запуска ***–f*** и верните параметр **max server memory** к предыдущему значению. Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
    
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может использовать память динамически; но можно установить параметры памяти вручную и ограничить объем памяти, доступный для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перед настройкой объема памяти для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определите подходящее значение путем вычитания из общего объема физической памяти того объема, который требуется операционной системе, выделениям памяти, не управляемым параметром max_server_memory, и другим экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (и для других нужд, если компьютер не выделен полностью под сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Разница — максимальный объем памяти, который можно выделить текущему экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 
## <a name="setting-the-memory-options-manually"></a>Настройка параметров памяти вручную  
Можно установить для параметров сервера **Мин. памяти сервера** и **Макс. памяти сервера** значения, покрывающие весь доступный объем памяти. Этот метод полезен для системных администраторов или администраторов баз данных, когда требуется настроить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] так, чтобы его параметры не противоречили требованиям к памяти других приложений или других экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запущенных на этом узле.

> [!NOTE]
> Параметры **min server memory** и **max server memory** являются расширенными. При использовании системной хранимой процедуры **sp_configure** для изменения этих настроек изменить их можно, только если параметр **show advanced options** установлен в значение 1. Эти параметры вступают в силу сразу же без перезагрузки сервера.  
  
<a name="min_server_memory"></a>Параметр **min_server_memory** используется для гарантированного предоставления минимального объема памяти, доступного диспетчеру памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не выделяет немедленно объем памяти, указанный в параметре **min server memory** , после запуска. Тем не менее, когда это значение достигается с ростом рабочей нагрузки, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может освободить память, выделенную буферному пулу, если не уменьшить значение параметра **min server memory** . Например, если на одном узле может находиться сразу несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], задайте параметр min_server_memory вместо max_server_memory, чтобы зарезервировать память для экземпляра. Кроме того, необходимо задать значение min_server_memory в виртуализированной среде, чтобы гарантировать, что при дефиците памяти на базовом узле не будет попыток выделить больше памяти из буферного пула в гостевой виртуальной машине [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чем это необходимо для приемлемой производительности.
 
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не гарантирует, что объем памяти, заданный параметром **min server memory**, будет выделен. Если нагрузка на сервер никогда не требует выделения всего объема памяти, заданного параметром **min server memory**, сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использовать меньше памяти.  
  
<a name="max_server_memory"></a> Параметр **max_server_memory** гарантирует, что в ОС не возникнет дефицит памяти. Чтобы задать конфигурацию "Макс. памяти сервера", отследите общее использование памяти процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и определите требования к памяти. Более точные вычисления для одного экземпляра
 -  Зарезервируйте 1–4 ГБ от общего объема памяти для ОС.
 -  Затем вычтите эквивалент потенциального выделения памяти ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), которое не входят в диапазон **Макс. памяти сервера**, состоящий из ***стека <sup>1</sup> * вычисляемое максимальное число рабочих потоков <sup>2</sup> + параметр загрузки -g <sup>3</sup>*** (или 256 МБ по умолчанию, если значение *-g* не задано). Остаток и даст значение параметра max_server_memory в случае установки одного экземпляра.
 
<sup>1</sup> Сведения о размерах стеков потока для различных архитектур см. в разделе [Руководство по архитектуре управления памятью](../../relational-databases/memory-management-architecture-guide.md#stacksizes).

<sup>2</sup> Сведения о вычислении рабочих потоков по умолчанию для заданного числа сходных ЦП на текущем узле см. в разделе [Настройка параметра конфигурации сервера "Максимальное число рабочих потоков"](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md).

<sup>3</sup> Сведения о параметре запуска *-g* см. на странице документации [Параметры запуска службы ядра СУБД](../../database-engine/configure-windows/database-engine-service-startup-options.md).

## <a name="how-to-configure-memory-options-using-includessmanstudiofullincludesssmanstudiofull-mdmd"></a>Настройка параметров памяти с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
Используйте два параметра памяти сервера, **Мин. памяти сервера** и **Макс. памяти сервера**, для настройки объема памяти (в мегабайтах), находящейся в управлении диспетчера памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может динамически изменять требования к памяти в зависимости от доступных системных ресурсов.  
  
### <a name="procedure-for-configuring-a-fixed-amount-of-memory-not-recommended"></a>Настройка фиксированного объема памяти (не рекомендуется)  
Установка фиксированного размера памяти  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Память** .  
  
3.  В пункте **Параметры памяти сервера** введите нужное значение в полях **Минимальный размер памяти сервера** и **Максимальный размер памяти сервера**.  
  
     Оставьте параметры по умолчанию, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] изменял требования к памяти динамически, исходя из доступности системных ресурсов. Рекомендуется задать для параметра **Макс. памяти сервера** значение, [указанное выше](#max_server_memory). 
  
## <a name="lock-pages-in-memory-lpim"></a>Блокировка страниц в памяти (LPIM) 
Эта политика Windows определяет, какие учетные записи могут использовать процесс для сохранения данных в физической памяти, чтобы система не отправляла страницы данных в виртуальную память на диске. Блокировка страниц в памяти может обеспечивать отклик сервера, когда содержимое памяти заносится в файл подкачки. Для параметра **Блокировка страниц в памяти** указывается значение "Включено" в экземплярах выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition и выше, если учетной записи с привилегией на выполнение sqlservr.exe предоставлено право пользователя Windows *Блокировка страниц в памяти* (LPIM).  
  
Чтобы отключить параметр **Блокировка страниц в памяти** для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], удалите право пользователя *Блокировка страниц в памяти* у учетной записи с привилегиями для запуска sqlservr.exe (стартовой учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).  
 
Задание этого параметра не повлияет на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [динамическое управление памятью](../../relational-databases/memory-management-architecture-guide.md#dynamic-memory-management), что позволит расширить или сузить ее по запросу других клерков памяти. При использовании пользовательского права *Блокировка страниц в памяти* рекомендуется задать верхний предел для параметра **Макс. памяти сервера**, как [указано выше](#max_server_memory).

> [!IMPORTANT]
> Задавать этот параметр следует, только если он необходим, то есть при наличии признаков того, что процесс sqlservr вытесняется из памяти. В этом случае в журнале ошибок появится ошибка 17890, как в примере ниже: `A significant part of sql server process memory has been paged out. This may result in a performance degradation. Duration: #### seconds. Working set (KB): ####, committed (KB): ####, memory utilization: ##%.` Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [флаг трассировки 845](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) не нужен для использования заблокированных страниц в выпуске Standard Edition. 
  
### <a name="to-enable-lock-pages-in-memory"></a>Включение блокировки страниц в памяти  
Включение параметра "Блокировка страниц в памяти"  
  
1.  В меню **Пуск** выберите команду **Выполнить**. В окне **Открыть** введите **gpedit.msc**.  
  
     Откроется диалоговое окно **Групповая политика** .  
  
2.  В консоли **Групповая политика** разверните узел **Конфигурация компьютера**, затем узел **Конфигурация Windows**.  
  
3.  Разверните узлы **Настройки безопасности**и **Локальные политики**.  
  
4.  Выберите папку **Назначение прав пользователя** .  
  
     Политики будут показаны на панели подробностей.  
  
5.  На этой панели дважды щелкните параметр **Блокировка страниц в памяти**.  
  
6.  В диалоговом окне **Параметр политики локальной защиты** добавьте учетную запись с правами запуска sqlservr.exe (стартовая учетная запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).  
  
## <a name="running-multiple-instances-of-includessnoversionincludesssnoversion-mdmd"></a>Запуск нескольких экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 При выполнении нескольких экземпляров компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]существует три подхода к управлению памятью.  
  
-   Используйте параметр **Макс. памяти сервера**, чтобы управлять использованием памяти, как [указано выше](#max_server_memory). Установите максимальные значения для каждого экземпляра, учитывая, что их сумма не должна превышать общий объем физической памяти, установленной на компьютере. Рекомендуется выделять каждому экземпляру объем памяти, пропорциональный его ожидаемой рабочей нагрузке или размеру базы данных. Данный подход имеет то преимущество, что свободная память доступна новым процессам или экземплярам сразу же после их запуска. Недостаток состоит в том, что, когда выполняются не все экземпляры, ни один из выполняющихся экземпляров не сможет использовать память, оставшуюся свободной.  
  
-   Используйте параметр **Мин. памяти сервера**, чтобы управлять использованием памяти, как [указано выше](#min_server_memory). Установите минимальные значения для каждого экземпляра так, чтобы их сумма была на 1-2 ГБ меньше общего объема физической памяти, установленной на компьютере. Рекомендуется выделять каждому экземпляру минимальный объем памяти, пропорциональный его ожидаемой рабочей нагрузке. Данный подход имеет то преимущество, что выполняющиеся экземпляры могут использовать оставшуюся свободную память в случае, когда выполняются не все экземпляры. Данный подход также полезен, когда на компьютере выполняется другой процесс, интенсивно потребляющий память, так как при этом обеспечивается удовлетворение как минимум заданных потребностей сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в памяти. Недостаток состоит в том, что при запуске нового экземпляра (или любого другого процесса) уже выполняющимся экземплярам требуется некоторое время для освобождения памяти, особенно если для этого им необходимо записать измененные страницы обратно в базу данных.  
  
-   Отсутствие действий (не рекомендуется). Первый экземпляр, столкнувшийся с рабочей нагрузкой, попытается захватить всю память. Простаивающие экземпляры или экземпляры, запущенные позже других, могут в конечном итоге быть вынуждены работать лишь с минимальным доступным объемом памяти. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не пытается равномерно распределять возможности использования памяти между экземплярами. Тем не менее все экземпляры будут реагировать на сигналы уведомлений памяти Windows, корректируя объемы используемой ими памяти. Операционная система Windows не балансирует память между приложениями с помощью уведомлений памяти API-интерфейса. Эти уведомления лишь обеспечивают глобальную обратную связь относительно доступности памяти в системе.  
  
 Эти настройки можно изменять без перезапуска экземпляров, поэтому можно легко экспериментировать с целью нахождения наиболее подходящих настроек для данной модели использования.  
  
## <a name="providing-the-maximum-amount-of-memory-to-sql-server"></a>Выделение максимального объема памяти для SQL Server  
Для всех выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] память можно выделять вплоть до предела виртуального адресного пространства процесса. Дополнительные сведения см. в разделе [Предельный объем памяти для выпусков Windows и Windows Server](http://msdn.microsoft.com/library/windows/desktop/aa366778(v=vs.85).aspx#physical_memory_limits_windows_server_2016).
  
## <a name="examples"></a>Примеры  
  
### <a name="example-a"></a>Пример A  
 В следующем примере параметр `max server memory` устанавливается равным 4 ГБ.  
  
```sql  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'max server memory', 4096;  
GO  
RECONFIGURE;  
GO  
```  
  
### <a name="example-b-determining-current-memory-allocation"></a>Пример Б. Определение текущего распределения памяти  
 Следующий запрос возвращает информацию о текущем распределении памяти.  
  
```sql  
SELECT 
  physical_memory_in_use_kb/1024 AS sql_physical_memory_in_use_MB, 
    large_page_allocations_kb/1024 AS sql_large_page_allocations_MB, 
    locked_page_allocations_kb/1024 AS sql_locked_page_allocations_MB,
    virtual_address_space_reserved_kb/1024 AS sql_VAS_reserved_MB, 
    virtual_address_space_committed_kb/1024 AS sql_VAS_committed_MB, 
    virtual_address_space_available_kb/1024 AS sql_VAS_available_MB,
    page_fault_count AS sql_page_fault_count,
    memory_utilization_percentage AS sql_memory_utilization_percentage, 
    process_physical_memory_low AS sql_process_physical_memory_low, 
    process_virtual_memory_low AS sql_process_virtual_memory_low
FROM sys.dm_os_process_memory;  
```  
  
## <a name="see-also"></a>См. также:  
 [Руководство по архитектуре управления памятью](../../relational-databases/memory-management-architecture-guide.md)   
 [Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md)   
 [Выпуски и поддерживаемые функции SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md#Cross-BoxScaleLimits)   
 [Выпуски и поддерживаемые функции SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md#Cross-BoxScaleLimits)   
 [Выпуски и поддерживаемые функции SQL Server 2017 в Linux](../../linux/sql-server-linux-editions-and-components-2017.md#Cross-BoxScaleLimits)   
 [Предельный объем памяти для выпусков Windows и Windows Server](http://msdn.microsoft.com/library/windows/desktop/aa366778(v=vs.85).aspx)
 
