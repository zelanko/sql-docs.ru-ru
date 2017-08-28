---
title: "Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS | Документы Microsoft"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dab69c7-73af-4340-aef0-de057356b791
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d7317cad5aa1e77653431c128ce1549bc4349e18
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этом разделе описывается выполнение пакетов служб SQL Server Integration Services (SSIS) для Linux. SSIS решает проблемы с интегрированием сложных данных, загрузка данных из нескольких источников и форматов, преобразования и очистки данных и обновление нескольких целевых серверов. 

Пакеты служб SSIS, выполняемым на платформе Linux можно подключиться к Microsoft SQL Server запущен на Windows локально или в облаке, в Linux или в Docker. Они также могут подключаться к базе данных SQL Azure, хранилище данных SQL Azure и источники данных ODBC.

Службы SSIS можно использовать для запуска пакетов в Linux, при наличии компьютера Windows для создания и обслуживания пакетов. Средства проектирования и управления служб SSIS будут приложений Windows. 

## <a name="prerequisites"></a>Предварительные требования

Для запуска пакетов служб SSIS на компьютере Linux, сначала необходимо установить SQL Server Integration Services. Инструкции по установке см. в разделе [установить SQL Server Integration Services](sql-server-linux-setup-ssis.md).

## <a name="run-an-ssis-package"></a>Запустить пакет служб SSIS

Чтобы запустить пакет служб SSIS на компьютере Linux, выполните следующие действия:

1.  Скопируйте пакет служб SSIS на компьютере Linux.
2.  Выполните следующую команду:
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="more-about-ssis-on-linux"></a>Дополнительные сведения о служб SSIS в Linux

**Подключения ODBC**. С помощью служб SSIS на Linux CTP-версии 2.1 обновления и более поздних версий пакетов служб SSIS можно использовать подключения ODBC в Linux. Эта функциональность была протестирована с SQL Server и драйверы MySQL ODBC, но также требуются для работы с любой драйвер ODBC Юникода, отслеживающее спецификации ODBC. Во время разработки укажите имя источника данных или строку подключения для подключения к данным ODBC; Можно также использовать проверку подлинности Windows. Дополнительные сведения см. в разделе [записи блога Представляем поддержка ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Пути**. Служб SSIS в Linux не поддерживает пути стиле Linux, но сопоставляет пути стиль Windows в стиле Linux пути во время выполнения. Предоставляют пути стиль Windows в пакеты служб SSIS. Затем, например, служб SSIS в Linux сопоставляет путь стиль Windows `C:\test` в стиле Linux путь `/test`.

**Развертывание пакетов**. Пакеты можно сохранить только в файловой системе на платформе Linux в этом выпуске. База данных каталога служб SSIS и устаревшие службы SSIS недоступны в Linux для хранения и развертывания пакетов.

**Планирование пакетов**. Для планирования выполнения пакетов в этом выпуске нельзя использовать агента SQL Server в Linux.

**Другие ограничения и известные проблемы**. Следующие функции не поддерживаются в этом выпуске при запуске пакетов служб SSIS в Linux:
  - База данных каталога служб SSIS
  - Выполнение запланированного пакета агентом SQL
  - Проверка подлинности Windows.
  - Компоненты сторонних разработчиков
  - Система отслеживания измененных данных (CDC)
  - Масштабирование служб SSIS
  - Пакет дополнительных компонентов Azure для служб SSIS
  - Поддержка Hadoop и HDFS
  - Соединитель Microsoft Connector для SAP BW

Другие ограничения и известные проблемы с помощью служб SSIS в Linux см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md#ssis).

Дополнительные сведения о служб SSIS в Linux см. в следующих записях блога:

-   [Служб SSIS для Linux доступна в SQL Server CTP2.1 2017 г.](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC поддерживается в службах SSIS в Linux (обновить SQL Server 2017 г CTP-версия 2.1)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-about-ssis"></a>Дополнительные сведения о служб SSIS

Microsoft SQL Server Integration Services (SSIS) — это платформа для создания решений интеграции данных высокой производительности, включая извлечения, преобразования и загрузки (ETL) пакетов для хранилищ данных. Дополнительные сведения о службах SSIS см. в разделе [Службы SQL Server Integration Services](/sql/integration-services/sql-server-integration-services.md).

Службы SSIS включает следующие компоненты:
- графические средства и мастера для построения и отладки пакетов в Windows
- широкий набор задач для выполнения функций потока операций, таких как операции FTP, выполнение инструкций SQL и отправка сообщений электронной почты
- различные источники данных и назначения для извлечения и загрузки данных
- разнообразие преобразований для очистки, статистической обработки, слияния и копирования данных
- программные интерфейсы (API) для расширения служб SSIS с помощью собственных пользовательских сценариев и компоненты

Чтобы приступить к работе со службами SSIS, загрузите последнюю версию [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md). Затем выполните учебника [служб SSIS, как создать ETL-пакета](https://msdn.microsoft.com/en-us/library/ms169917.aspx).

## <a name="see-also"></a>См. также:
- [Дополнительные сведения о SQL Server Integration Services](https://msdn.microsoft.com/en-us/library/ms141026.aspx)
- [SQL Server Integration Services (SSIS) разработки и средства управления](https://msdn.microsoft.com/en-us/library/ms140028.aspx)
- [SQL Server Integration Services, учебники](https://msdn.microsoft.com/en-us/library/jj720568.aspx)

