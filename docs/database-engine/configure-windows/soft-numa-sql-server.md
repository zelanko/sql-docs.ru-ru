---
title: "Архитектура Soft-NUMA (SQL Server) | Документы Майкрософт"
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NUMA
- soft-NUMA
helpviewer_keywords:
- NUMA
- non-uniform memory access
- soft-NUMA
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
caps.latest.revision: "53"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: adde08cc4584568c42d896b70ffbcc49689d6416
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="soft-numa-sql-server"></a>Архитектура Soft-NUMA (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Современные процессоры имеют несколько или множество ядер на одном сокете. Каждый сокет обычно представлен одним узлом NUMA. Ядро базы данных SQL Server секционирует разные внутренние структуры и потоки служб в узлы NUMA.  Если используются процессоры с 10 и более ядрами на сокет, распределение нагрузки между аппаратными узлами NUMA с помощью программной архитектуры NUMA зачастую позволяет повысить масштабируемость и производительность системы. До SQL Server 2014 с пакетом обновления 2 (SP2) для использования программной архитектуры NUMA (Soft-NUMA) нужно было редактировать реестр, чтобы добавить маску сходства для настройки узла. Такая настройка выполнялась для каждого компьютера, а не для экземпляра.  SQL Server 2014 с пакетом обновления 2 (SP2) и SQL Server 2016 автоматически настраивают архитектуру Soft-NUMA на уровне экземпляра базы данных при запуске службы SQL Server.  
  
> [!NOTE]  
>  Архитектура Soft-NUMA не поддерживает процессоры с "горячей" заменой.  
  
## <a name="automatic-soft-numa"></a>Автоматическое создание архитектуры Soft-NUMA  
 По умолчанию в SQL Server 2016 сервер ядра базы данных автоматически создает узлы архитектуры Soft-NUMA, если во время запуска обнаруживает более 8 физических ядер на один сокет или узел NUMA. Процессорные ядра с технологией Hyper-Threading не различаются при подсчете физических ядер на узле.  Если обнаружено больше 8 физических ядер на один сокет, служба ядра базы данных создает узлы архитектуры Soft-NUMA. В идеале узлы содержат по 8 ядер, но поддерживают и другое количество — от 5 до 9 логических ядер на один узел. Размер аппаратного узла может быть ограничен маской сходства ЦП. См.   
            [ALTER SERVER CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-server-configuration-transact-sql.md). Количество узлов NUMA не может превышать максимальное количество поддерживаемых узлов NUMA.  
  
 Использование архитектуры Soft-NUMA можно отключать и включать с помощью инструкции [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md) с аргументом SET SOFTNUMA. Чтобы изменение этого параметра вступило в силу, потребуется перезапустить ядро базы данных.  
  
 На рисунке ниже показан пример сведений об архитектуре Soft-NUMA, которые вы увидите в журнале ошибок SQL Server, если SQL Server обнаружит аппаратные узлы NUMA с более чем 8 физическими ядрами для каждого узла или сокета.  


``2016-11-14 13:39:43.17 Server      SQL Server detected 2 sockets with 12 cores per socket and 24 logical processors per socket, 48 total logical processors; using 48 logical processors based on SQL Server licensing. This is an informational message; no user action is required.``  
  **``2016-11-14 13:39:43.35 Server      Automatic soft-NUMA was enabled because SQL Server has detected hardware NUMA nodes with greater than 8 physical cores.``**  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 0: CPU mask: 0x0000000000555555:0 Active CPU mask: 0x0000000000555555:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 1: CPU mask: 0x0000000000aaaaaa:0 Active CPU mask: 0x0000000000aaaaaa:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 2: CPU mask: 0x0000555555000000:0 Active CPU mask: 0x0000555555000000:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 3: CPU mask: 0x0000aaaaaa000000:0 Active CPU mask: 0x0000aaaaaa000000:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``

  
## <a name="manual-soft-numa"></a>Создание архитектуры Soft-NUMA вручную  
 Вы можете вручную настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для использования архитектуры Soft-NUMA. Для этого нужно отключить автоматическую настройку архитектуры Soft-NUMA и добавить в реестре маску сходства для настройки узла. Маска архитектуры Soft-NUMA в этом случае указывается как запись реестра с двоичным типом данных, типом данных DWORD (шестнадцатеричным или десятичным) или QWORD (шестнадцатеричным или десятичным). Чтобы настроить большее количество процессоров (больше чем первые 32), используйте значения реестра QWORD или BINARY. (Значения QWORD нельзя использовать до [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].) Отредактировав реестр, перезапустите [!INCLUDE[ssDE](../../includes/ssde-md.md)], чтобы конфигурация архитектуры Soft-NUMA вступила в силу.  
  
> [!TIP]
> Нумерация процессоров начинается с 0.  

> [!WARNING]
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 Рассмотрим следующий пример. В этом примере компьютер с восемью процессорами не имеет оборудования NUMA. Настраиваются три узла программной архитектуры NUMA.   
            Экземпляр А компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] настраивается для использования процессоров в количестве от 0 до 3. Второй экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлен и настроен для использования процессоров с 4 до 7. Визуально пример может быть представлен следующим образом.  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 Экземпляр А, испытывающий значительные нагрузки ввода-вывода, имеет теперь два потока ввода-вывода и один поток модуля отложенной записи, в то время как экземпляр В, выполняющий операции с интенсивным использованием процессора, имеет только один поток ввода-вывода и один поток модуля отложенной записи. Экземплярам может быть выделено различное количество памяти, но в отличие от оборудования NUMA, они оба получают память из одного блока памяти операционной системы, и здесь нет соответствия памяти и процессора.  
  
 Поток модуля отложенной записи связан с представлением физических узлов памяти NUMA в операционной системе SQL. Поэтому любое число единиц оборудования, представленного как физические узлы NUMA, будет равным числу создаваемых потоков модуля отложенной записи. Дополнительные сведения см. в разделе   
            [Принцип работы: программная архитектура Soft NUMA, поток завершения ввода-вывода, рабочие процессы отложенной записи и узлы памяти](http://blogs.msdn.com/b/psssql/archive/2010/04/02/how-it-works-soft-numa-i-o-completion-thread-lazy-writer-workers-and-memory-nodes.aspx).  
  
> [!NOTE]
> Разделы реестра **Soft-NUMA** не копируются при обновлении экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="set-the-cpu-affinity-mask"></a>Установка маски схожести ЦП  
 Выполните следующую инструкцию в экземпляре А, чтобы настроить его для использования процессоров 0, 1, 2 и 3 путем задания маски схожести ЦП.  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=0 TO 3;  
```  
  
 Выполните следующую инструкцию в экземпляре В, чтобы настроить его для использования процессоров 4, 5, 6 и 7 путем задания маски схожести ЦП.  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=4 TO 7;  
```  
  
### <a name="map-soft-numa-nodes-to-cpus"></a>Установка соответствия программной архитектуры NUMA нескольким процессорам  
 С помощью программы редактора реестра (regedit.exe) добавьте следующие разделы реестра, чтобы установить соответствие между узлом 0 программной архитектуры NUMA и процессорами ЦП0 и ЦП1, узлом 1 программной архитектуры NUMA и процессорами ЦП2 и ЦП3, а также узлом 2 и процессором ЦП4. 5, 6 и 7.  
  
> [!TIP]
> Чтобы указать процессоры с 60 по 63, используйте значение QWORD F000000000000000 или значение BINARY 1111000000000000000000000000000000000000000000000000000000000000.  
  
 В следующем примере предположим, что имеется сервер DL580 G9 с 18 ядрами на сокет (в 4 сокетах) и каждый сокет находится в собственной K-группе. Конфигурация программной архитектуры NUMA, которую можно создать, выглядит примерно следующим образом. (6 ядер на узел, по 3 узла в группе, 4 группы).  
  
|Пример для сервера [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с несколькими K-группами|Тип|Имя значения|Данные|  
|-----------------------------------------------------------------------------------------------------------------|----------|----------------|----------------|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node0|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node0|DWORD|Группирование|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node1|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node1|DWORD|Группирование|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node2|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node2|DWORD|Группирование|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node3|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node3|DWORD|Группирование|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node4|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node4|DWORD|Группирование|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node5|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node5|DWORD|Группирование|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node6|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node6|DWORD|Группирование|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node7|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node7|DWORD|Группирование|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node8|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node8|DWORD|Группирование|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node9|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node9|DWORD|Группирование|3|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node10|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node10|DWORD|Группирование|3|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node11|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node11|DWORD|Группирование|3|  
  
## <a name="metadata"></a>Метаданные  
 Для просмотра текущего состояния и конфигурации архитектуры Soft-NUMA можно использовать следующие динамические административные представления.  
  
-   [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md): отображает текущее значение (0 или 1) для SOFTNUMA  
  
-   [sys.dm_os_nodes (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql.md): столбец node_state_desc для каждого узла NUMA показывает, был ли этот узел создан архитектурой soft-NUMA.  
  
-   [sys.dm_os_sys_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md): в столбцах softnuma и softnuma_desc показаны значения конфигурации.  
  
> [!NOTE]
> Можно просмотреть текущее значение для автоматического создания программной архитектуры NUMA с помощью инструкции [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md), но изменить это значение с помощью **sp_configure** невозможно. Необходимо использовать инструкцию [ALTER SERVER CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-server-configuration-transact-sql.md) с аргументом SET SOFTNUMA.  
  
## <a name="see-also"></a>См. также  
 [Сопоставление портов TCP/IP с узлами NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/map-tcp-ip-ports-to-numa-nodes-sql-server.md)   
 [Параметр конфигурации сервера affinity mask](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md)  
  
  

