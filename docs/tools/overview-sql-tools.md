---
title: Обзор средств SQL
description: Средства для выполнения SQL-запросов и управления для SQL Server, SQL Azure (база данных SQL Azure, управляемый экземпляр SQL Azure, виртуальные машины SQL) и хранилища данных SQL Azure.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 02/04/2020
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 59a376b17c6e4b396dba24999a52bf37ecc27988
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009608"
---
# <a name="sql-tools-overview"></a>Обзор средств SQL

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Для управления базой данных требуется средство. Независимо от того, работают ли ваши базы данных в облаке, в Windows, в macOS или [Linux](../linux/sql-server-linux-overview.md), средство не нужно запускать на той же платформе, что и база данных.

Ссылки на различные средства SQL можно просмотреть в следующих таблицах.

> [!Note]
> Сведения о скачивании SQL Server см. в статье [Руководство по установке SQL Server](../database-engine/install-windows/install-sql-server.md).

## <a name="recommended-tools"></a>Рекомендуемые средства

Следующие средства предоставляют графический пользовательский интерфейс (GUI).

| Инструмент | Description | Операционная система |
|:--|:--|:--|
| [ **![Изображение ADS](../tools/media/overview-sql-tools/azure-data-studio.svg)</br></br>Azure Data Studio**](../azure-data-studio/download.md) | Простой редактор, с помощью которого можно выполнять SQL-запросы по требованию, а затем анализировать и сохранять результаты в виде текста, а также в форматах JSON или Excel. Редактируйте данные, упорядочивайте избранные подключения к базам данных и просматривайте объекты базы данных в знакомом интерфейсе. | **Windows</br>macOS</br>Linux** |
| [ **![Изображение SSMS](../tools/media/overview-sql-tools/ssms.svg)</br></br>SQL Server Management Studio (SSMS)** ](../ssms/download-sql-server-management-studio-ssms.md) | Управление экземпляром SQL Server или базой данных с полной поддержкой GUI. Возможности доступа, настройки, администрирования и разработки всех компонентов SQL Server, Базы данных SQL Azure и хранилища данных SQL, а также управления ими. Среда SSMS предоставляет единую полнофункциональную служебную программу, которая сочетает в себе обширную группу графических инструментов с рядом отличных редакторов сценариев для доступа к службе SQL Server для разработчиков и администраторов баз данных всех профессиональных уровней. | **Windows** |
| [ **![Изображение SSDT](../tools/media/overview-sql-tools/ssdt.svg)</br>SQL Server Data Tools (SSDT)** ](../ssdt/download-sql-server-data-tools-ssdt.md) | Это современное средство разработки, позволяющее создавать реляционные базы данных SQL Server, базы данных SQL Azure, модели данных Analysis Services (AS), пакеты Integration Services (IS) и отчеты Reporting Services (RS). С помощью SSDT вы можете проектировать и развертывать любые типы содержимого SQL Server так же просто, как разрабатывать приложения в **[Visual Studio](https://visualstudio.microsoft.com/downloads/)** . | **Windows** |
| [ **![Изображение VS Code](../tools/media/overview-sql-tools/visual-studio-code.svg)</br></br>Visual Studio Code**](https://code.visualstudio.com/) | **[Расширение mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)** для Visual Studio Code — это официальное расширение SQL Server, которое поддерживает подключения к SQL Server и расширенные возможности редактирования для T-SQL в Visual Studio Code. Написание скриптов T-SQL в упрощенном редакторе. | **Windows</br>macOS</br>Linux** |

## <a name="command-line-tools"></a>Программы командной строки

Ниже приведены основные средства командной строки.

| Инструмент | Description | Операционная система |
|:--|:--|:--|
|[**bcp**](bcp-utility.md)|Служебная программа **b**ulk **c**opy **p**rogram (**bcp**) используется для массового копирования данных между экземпляром [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и файлом данных в указанном пользователем формате.| **Windows</br>macOS</br>Linux** |
|[**mssql-cli (предварительная версия)** ](mssql-cli.md)|**mssql-cli** представляет собой интерактивное средство создания запросов к SQL Server из командной строки. Кроме того, SQL Server можно запрашивать с помощью программы командной строки, в которой реализована технология IntelliSense, выделение синтаксиса и многое другое. | **Windows</br>macOS</br>Linux** |
|[**mssql-conf**](../linux/sql-server-linux-configure-mssql-conf.md) | Средство **mssql-conf** настраивает SQL Server в Linux. | **Linux** |
|[**mssql-scripter (предварительная версия)** ](https://github.com/Microsoft/mssql-scripter) | **mssql-scripter** — это многоплатформенный интерфейс командной строки для написания сценариев баз данных SQL Server. | **Windows</br>macOS</br>Linux** |
| [**sqlcmd**](sqlcmd-utility.md) |Служебная программа **sqlcmd** позволяет из командной строки выполнять инструкции Transact-SQL, системные процедуры и файлы скриптов. | **Windows</br>macOS</br>Linux** |
| [**sqlpackage**](sqlpackage.md) |Программа командной строки **sqlpackage** автоматизирует некоторые задачи разработки баз данных. |**Windows</br>macOS</br>Linux** |
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** предоставляет командлеты для работы с SQL. | **Windows</br>macOS</br>Linux** |

## <a name="migration-and-other-tools"></a>Средства миграции и другие инструменты

Эти средства используются для переноса, настройки и предоставления других функций для баз данных SQL.

| Инструмент | Description |
|:--|:--|
| **[Диспетчер конфигураций](../tools/configuration-manager/sql-server-configuration-manager-help.md)** | Используйте диспетчер конфигурации SQL Server, чтобы настроить службы SQL Server и сетевые соединения. Configuration Manager работает в Windows.|
| **[Database Experimentation Assistant](../dea/database-experimentation-assistant-overview.md)** | Database Experimentation Assistant позволяет оценить целевую версию SQL для данной рабочей нагрузки. |
| **[Помощник по миграции данных](../dma/dma-overview.md)** | Помощник по миграции данных поможет вам выполнить переход на современную платформу данных благодаря обнаружению проблем совместимости, которые могут влиять на функциональные возможности базы данных в новой версии SQL Server или базы данных SQL Azure. |
| **[Распределенное воспроизведение](../tools/distributed-replay/install-distributed-replay-overview.md)** | Функция распределенного воспроизведения позволяет оценить влияние будущих обновлений SQL Server. Ее также можно использовать для оценки влияния обновлений аппаратной части и операционной системы, а также для настройки SQL Server. |
| **[ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)** | Программа ssbdiagnose сообщает о проблемах в диалогах Service Broker или в конфигурации служб Service Broker. |
| **[Помощник по миграции SQL Server](../ssma/sql-server-migration-assistant.md)** | Помощник по миграции SQL Server используется для автоматизации миграции баз данных в SQL Server из Microsoft Access, DB2, MySQL, Oracle и Sybase.|

Если вы ищете дополнительные средства, которые не упоминаются на этой странице, ознакомьтесь со статьями [Служебные программы командной строки SQL (ядро СУБД)](command-prompt-utility-reference-database-engine.md) и [Скачивание расширенных компонентов и средств SQL Server](download-sql-feature-packs.md).