---
title: "Взаимодействие R R служб SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0506b950-34b3-4f11-8e2f-d067a58015bd
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Взаимодействие R R служб SQL Server

Этот раздел посвящен механизм для запуска для R в [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], и описываются различия между Microsoft R и открытым исходным кодом R. Сведения о дополнительных компонентах см. в разделе [новых компонентов в SQL Server](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md).

### Компоненты с открытым исходным кодом R

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] включает полный распространения базовые пакеты R и средств. Дополнительные сведения о том, что входят в состав базового распространения см. в документации, установленный во время установки в папке по умолчанию:
`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`

Как часть установки [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], должен дать согласие с условиями публичной лицензии GNU. После этого можно выполнять стандартные пакеты R без дальнейших изменений так же, как и в других открытого распределение R.

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Среда выполнения R никоим образом не изменяется. Среда выполнения R выполняется за пределами [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] обработки и может выполняться независимо от [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Однако настоятельно рекомендуется не запускать эти средства при [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] с помощью R, чтобы избежать конфликта ресурсов.

Распределение базовый пакет R, связанный с конкретным [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] экземпляра можно найти в папке, связанной с экземпляром. Например, если установлены службы R на экземпляре по умолчанию, библиотеки R находятся в `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`.

Аналогично, R средствами, связанными с экземпляром по умолчанию будут размещены в `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`,

Дополнительные сведения о распределении базовый см [пакеты, установленные с Microsoft R Open](https://mran.revolutionanalytics.com/rro/installed/)

### Пакеты дополнительных R

В дополнение к базовым распространения R [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] включает некоторые собственные пакеты R, а также платформа для параллельного выполнения R и библиотек, поддерживающих выполнение R в контексте удаленного вычислений. 

Этот объединенный набор компонентов R - R базового распределения, а также улучшенные R компонентов и пакетов - называется **Microsoft R**. При установке Microsoft Server R (автономный) можно получить именно тот же набор пакетов, установленных в службах SQL Server R (в базы данных), но в другой папке. 

Microsoft R включает распространения математических библиотек ядра Intel, который используется по возможности быстрее математические обработки. Например Библиотека базовых линейной алгебры (BLAS) используется для многих пакетах надстроек, а также R сам. Дополнительные сведения см. в статьях:

+ [Как математические ядра Intel ускоряет R](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html)
+ [Повышение производительности для связывания R для многопоточных математических библиотек](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html)

Среди наиболее важные дополнения к Microsoft R **RevoScaleR** и **RevoPemaR** пакетов. Это пакетов R, которые были записаны во многом в C или C++ для повышения производительности.

+ **RevoScaleR.** Включает различные интерфейсы API для анализа и обработки данных. API-интерфейсы оптимизированы для анализа наборов данных, которые слишком велики для размещения в памяти и для выполнения вычислений, распределенные по несколько ядер или процессоров.

   RevoScaleR API-интерфейсы также поддерживают работу с подмножествами данных для улучшения масштабируемости. Другими словами большинство функций RevoScaleR может работать на блоки данных и обновление алгоритмы выполнять статистическую обработку результатов. Таким образом R решения, основанные на функции RevoScaleR может работать с очень большими наборами данных и не связаны с локальной памяти.

  Также поддерживает RevoScaleR пакета. Формат файла XDF быстрее перемещения и хранения данных, используемых для анализа. Формат XDF использует хранилище столбцов, является переносимым и может использоваться для загрузки и затем обрабатывают данные из различных источников, включая текст, SPSS или подключения ODBC. Пример использования формата XDF содержится в этом учебнике: [подробный обзор обработки и анализа данных](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)


+ **RevoPemaR.** PEMA расшифровывается как параллельный алгоритм внешней памяти.  **RevoPemaR** пакет предоставляет интерфейсы API, которые можно использовать для разработки собственных параллельных алгоритмов. Дополнительные сведения см. в разделе [RevoPemaR руководство по началу работы](https://msdn.microsoft.com/microsoft-r/rserver/rserver-pemar-getting-started).

## См. также:
[Обзор архитектуры](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)

[Новые компоненты SQL Server для поддержки служб R](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)

[Общие сведения о безопасности](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md)
