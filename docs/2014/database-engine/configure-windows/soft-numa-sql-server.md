---
title: Настройка SQL Server для использования архитектуры Soft-NUMA (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 07/12/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- non-uniform memory access
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
caps.latest.revision: 38
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 434e569b17fa70b6f6b3f4763e54e08e271dc99b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279566"
---
# <a name="configure-sql-server-to-use-soft-numa-sql-server"></a>Настройка использования программной архитектуры NUMA (SQL Server) в SQL Server
Современные процессоры имеют несколько или множество ядер на одном сокете. Каждый сокет обычно представлен одним узлом NUMA. Ядро базы данных SQL Server секционирует разные внутренние структуры и потоки служб в узлы NUMA. С процессорами, содержащий 10 и более ядрами на сокет, с помощью программного обеспечения NUMA (soft-NUMA) для разделения узлами оборудования NUMA, обычно повышает производительность и масштабируемость.   

> [!NOTE]
> Архитектура Soft-NUMA не поддерживает процессоры с "горячей" заменой.
  
## <a name="automatic-soft-numa"></a>Автоматическое создание архитектуры Soft-NUMA

Начиная с SQL Server 2014 с пакетом обновления 2, каждый раз, когда сервер ядра базы данных обнаруживает более 8 физических процессоров, при запуске, программной архитектуры NUMA создаются автоматически, если флаг трассировки 8079 включен в качестве параметра запуска. Количество ядер процессора с поддержкой технологии Hyper Threading, не учитываются при подсчете физических процессоров. При число физических процессоров, которые обнаружил составляет более чем 8 для каждого сокета, службе компонента database engine создает узлы архитектуры soft-NUMA, в идеале содержат по 8 ядер, но можно перейти к 5 или до 9 логических процессоров на узел. Размер аппаратного узла может быть ограничен маской сходства ЦП. Количество узлов NUMA не может превышать максимальное количество поддерживаемых узлов NUMA.

Без флага трассировки soft-NUMA отключен по умолчанию. Вы можете включить программной архитектуры NUMA с помощью флага трассировки 8079. Чтобы изменение этого параметра вступило в силу, потребуется перезапустить ядро базы данных.

На следующем рисунке показан тип сведений об архитектуре soft-NUMA, которое будет отображаться в журнале ошибок SQL Server, когда SQL Server обнаружит аппаратные узлы NUMA с более чем 8 логических процессоров, если флаг трассировки 8079 включен.

![Soft-NUMA](./media/soft-numa-sql-server/soft-numa.PNG)

## <a name="manual-soft-numa"></a>Создание архитектуры Soft-NUMA вручную
  
Чтобы настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для использования архитектуры soft-NUMA вручную, необходимо изменить реестр, чтобы добавить маску схожести настройки узла. Маска программной архитектуры NUMA может быть задана как запись реестра, имеющая двоичный тип данных, тип данных DWORD (шестнадцатеричный или десятичный) или QWORD (шестнадцатеричный или десятичный). Чтобы настроить большее количество процессоров (больше чем первые 32), используйте значения реестра QWORD или BINARY. (Значения QWORD нельзя использовать до [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].) Для настройки программной архитектуры NUMA необходимо перезапустить компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
> [!TIP]  
>  Нумерация процессоров начинается с 0.  
  
 [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 Рассмотрим следующий пример. В этом примере компьютер с восемью процессорами не имеет оборудования NUMA. Настраиваются три узла программной архитектуры NUMA. Экземпляр А компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] настраивается для использования процессоров в количестве от 0 до 3. Второй экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлен и настроен для использования процессоров с 4 до 7. Визуально пример может быть представлен следующим образом.  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 Экземпляр А, испытывающий значительные нагрузки ввода-вывода, имеет теперь два потока ввода-вывода и один поток модуля отложенной записи, в то время как экземпляр В, выполняющий операции с интенсивным использованием процессора, имеет только один поток ввода-вывода и один поток модуля отложенной записи. Экземплярам может быть выделено различное количество памяти, но в отличие от оборудования NUMA, они оба получают память из одного блока памяти операционной системы, и здесь нет соответствия памяти и процессора.  
  
 Поток модуля отложенной записи связан с представлением физических узлов памяти NUMA в операционной системе SQL. Поэтому любое число единиц оборудования, представленного как физические узлы NUMA, будет равным числу создаваемых потоков модуля отложенной записи. Дополнительные сведения см. в разделе [Как это работает: программная архитектура NUMA, поток завершения ввода-вывода, рабочие процессы отложенной записи и узлы памяти](http://blogs.msdn.com/b/psssql/archive/2010/04/02/how-it-works-soft-numa-i-o-completion-thread-lazy-writer-workers-and-memory-nodes.aspx).  
  
> [!NOTE]  
>  Разделы реестра **Soft-NUMA** не копируются при обновлении экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="set-the-cpu-affinity-mask"></a>Установка маски схожести ЦП  
  
1.  Выполните следующую инструкцию в экземпляре А, чтобы настроить его для использования процессоров 0, 1, 2 и 3 путем задания маски схожести ЦП.  
  
    ```  
    ALTER SERVER CONFIGURATION   
    SET PROCESS AFFINITY CPU=0 TO 3;  
    ```  
  
2.  Выполните следующую инструкцию в экземпляре В, чтобы настроить его для использования процессоров 4, 5, 6 и 7 путем задания маски схожести ЦП.  
  
    ```  
    ALTER SERVER CONFIGURATION   
    SET PROCESS AFFINITY CPU=4 TO 7;  
    ```  
  
### <a name="map-soft-numa-nodes-to-cpus"></a>Установка соответствия программной архитектуры NUMA нескольким процессорам  
  
-   С помощью программы редактора реестра (regedit.exe) добавьте следующие разделы реестра, чтобы установить соответствие между узлом 0 программной архитектуры NUMA и процессорами ЦП0 и ЦП1, узлом 1 программной архитектуры NUMA и процессорами ЦП2 и ЦП3, а также узлом 2 и процессором ЦП4. 5, 6 и 7.  
  
     В следующем примере предположим, что имеется сервер DL580 G9 с 18 ядрами на сокет (в 4 сокетах) и каждый сокет находится в собственной K-группе. Конфигурация программной архитектуры NUMA, которую можно создать, выглядит примерно следующим образом. (6 ядер на узел, по 3 узла в группе, 4 группы).  
  
    |Пример для сервера [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с несколькими K-группами|Тип|Имя значения|Данные|  
    |------------------------------------------------------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Группирование|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Группирование|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Группирование|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|Группирование|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|Группирование|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|Группирование|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|Группирование|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|Группирование|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|Группирование|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|Группирование|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|Группирование|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|Группирование|3|  
  
     Дополнительные примеры  
  
    |[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Тип|Имя значения|Данные|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Группирование|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Группирование|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Группирование|0|  
  
    > [!TIP]  
    >  Чтобы указать процессоры с 60 по 63, используйте значение QWORD F000000000000000 или значение BINARY 1111000000000000000000000000000000000000000000000000000000000000.  
  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|Тип|Имя значения|Данные|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|Группирование|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|Группирование|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|Группирование|0|  
  
    |SQL Server 2008 R2|Тип|Имя значения|Данные|  
    |------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|Группирование|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|Группирование|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|Группирование|0|  
  
    |SQL Server 2008|Тип|Имя значения|Данные|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
    |SQL Server 2005|Тип|Имя значения|Данные|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление портов TCP/IP с узлами NUMA &#40;SQL Server&#41;](map-tcp-ip-ports-to-numa-nodes-sql-server.md)   
 [Параметр конфигурации сервера affinity mask](affinity-mask-server-configuration-option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
