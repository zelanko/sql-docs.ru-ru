---
title: "Использование среды SSMS для управления SQL Server для Linux | Документы Microsoft"
description: 
author: rothja
ms.author: jroth
manager: craigg
ms.date: 08/23/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.technology: database-engine
ms.assetid: b2fcf858-21c3-462a-8d49-50c85647d092
ms.custom: sql-linux
ms.workload: On Demand
ms.openlocfilehash: 31bff0cb43048585fb03246b683ad71e673bb7f4
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="use-sql-server-management-studio-on-windows-to-manage-sql-server-on-linux"></a>Использование среды SQL Server Management Studio в Windows для управления SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описаны [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) и будет выполнено несколько типичных задач. SSMS — это приложение Windows, поэтому SSMS следует использовать при наличии компьютером Windows, можно подключиться к удаленному экземпляру SQL Server в Linux.

[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) входит в набор средств SQL, которые корпорация Microsoft предлагает бесплатно для задач разработки и управления. Среда SSMS — это интегрированная среда для доступа, настройки, управления, администрирования и разработки всех компонентов SQL Server, работающий локально или в облаке, в Linux, Windows или Docker на macOS и базы данных SQL Azure и хранилище данных SQL Azure. Среда SSMS объединяет большое число графических средств с несколькими расширенными редакторами скриптов для предоставления доступа к SQL Server для разработчиков и администраторов с любым опытом.

Среда SSMS предлагает широкий спектр возможностей разработки и управления для SQL Server, включая средства:

- Настройка, отслеживать и администрировать одного или нескольких экземпляров SQL Server
- развертывание, мониторинг и обновления компонентов уровня данных, таких как базы данных и хранилищ данных
- резервное копирование и восстановление баз данных
- Построение и выполнение запросов T-SQL и скриптов и просмотреть результаты
- Создание скриптов T-SQL для объектов базы данных
- Просмотр и изменение данных в базах данных
- визуальное проектирование запросов T-SQL и объектов базы данных, такие как представления, таблицы и хранимые процедуры

В разделе [использования SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/ms174173.aspx) для получения дополнительной информации.

## <a name="install-the-newest-version-of-sql-server-management-studio-ssms"></a>Установите последнюю версию служб SQL Server Management Studio (SSMS)

При работе с SQL Server, следует всегда использовать последнюю версию служб SQL Server Management Studio (SSMS). Последнюю версию SSMS постоянно обновляется и оптимизированы и в настоящее время работает с SQL Server 2017 в Linux. Чтобы загрузить и установить последнюю версию, в разделе [загрузка SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Быть в курсе событий, последняя версия SSMS предлагает при наличии доступного для загрузки новой версии. 

## <a name="before-you-begin"></a>Перед началом
- В разделе [используйте SSMS в Windows для подключения к SQL Server в Linux](sql-server-linux-develop-use-ssms.md) способ подключения и запроса с помощью среды SSMS
- Чтение [известные проблемы](sql-server-linux-release-notes.md) для SQL Server 2017 г. в Linux

## <a name="create-and-manage-databases"></a>Создание и управление базами данных
При подключении к *master* базы данных, можно создавать базы данных на сервере и изменить или удалить существующие базы данных. Далее описывается, как выполнить несколько общие задачи управления базами данных через среду Management Studio. Для выполнения этих задач, убедитесь, что вы подключены к *master* базы данных с именем входа субъекта серверного уровня, созданный при настройке 2017 г. SQL Server в Linux.

### <a name="create-a-new-database"></a>Создание базы данных

1. Запустите SSMS и подключитесь к серверу в 2017 г. SQL Server в Linux

2. В обозревателе объектов щелкните правой кнопкой мыши *баз данных* папки, а затем нажмите кнопку * Создать базу данных...»

3. В *новую базу данных* диалоговое окно, введите имя новой базы данных, а затем нажмите кнопку *ОК*

Новая база данных успешно создан на сервере. Если вы предпочитаете создать новую базу данных с помощью T-SQL, а затем в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../t-sql/statements/create-database-sql-server-transact-sql.md).

### <a name="drop-a-database"></a>Удаление базы данных

1. Запустите SSMS и подключитесь к серверу в 2017 г. SQL Server в Linux

2. В обозревателе объектов разверните *баз данных* папку, чтобы просмотреть список всех баз данных на сервере.

3. В обозревателе объектов щелкните правой кнопкой мыши базу данных, следует удалить и нажмите кнопку *удалить*

4. В *удаление объекта* диалогового окна, проверка *закрыть существующие соединения* и нажмите кнопку *ОК*

База данных успешно удалена с сервера. Если вы предпочитаете удалить базу данных с помощью T-SQL, а затем в разделе [DROP DATABASE (SQL Server Transact-SQL)](../t-sql/statements/drop-database-transact-sql.md).

## <a name="use-activity-monitor-to-see-information-about-sql-server-activity"></a>Чтобы получить сведения об активности сервера SQL используйте монитора активности

[Монитора активности](../relational-databases/performance-monitor/activity-monitor.md) средство встроена в SQL Server Management Studio (SSMS) и отображает сведения о процессах SQL Server и как эти процессы влияют на текущий экземпляр SQL Server.

1. Запустите SSMS и подключитесь к серверу в 2017 г. SQL Server в Linux

2. В обозревателе объектов щелкните правой кнопкой мыши *сервера* , а затем щелкните *монитора активности*

Монитор активности показывает развертываемыми и свертываемыми панелями с следующие сведения:
- Обзор
- Процессы
- Ожидание ресурсов
- Данные файлового ввода-вывода
- Последние ресурсоемкие запросы
- Текущие ресурсоемкие запросы

При разворачивании панели монитор активности выполняет запрос к экземпляру сведения. При свертывании панели выполнение всех операций запроса для этой панели приостанавливается. Вы можете развернуть одну или несколько областей, в то же время для просмотра различных типов активности в экземпляре.

## <a name="see-also"></a>См. также:
- [Использование среды SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/ms174173.aspx)
- [Экспорт и импорт базы данных с помощью SSMS](sql-server-linux-migrate-ssms.md)
- [Руководство: SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/bb934498.aspx)
- [Учебник. Составление инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)
- [Производительность сервера и мониторинг активности](../relational-databases/performance/server-performance-and-activity-monitoring.md)
