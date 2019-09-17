---
title: SQL Query and Management Tools for SQL Server, Azure SQL (базы данных SQL Azure, управляемые экземпляры SQL Azure, виртуальные машины, работающие SQL) и хранилище данных SQL Azure | Документация Майкрософт
description: SQL Query and Management Tools for SQL Server, Azure SQL (база данных SQL Azure, управляемый экземпляр SQL Azure, виртуальные машины SQL) и хранилище данных SQL Azure
ms.custom: ''
ms.date: 09/11/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ''
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 56ed7a0cf53a026b470c90c36b37da95f02ac5bc
ms.sourcegitcommit: 3bd813ab2c56b415a952e5fbd5cfd96b361c72a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913567"
---
# <a name="sql-query-and-management-tools-for-sql-server-azure-sql-azure-sql-database-azure-sql-managed-instance-sql-virtual-machines-and-azure-sql-data-warehouse"></a>SQL Query and Management Tools for SQL Server, Azure SQL (база данных SQL Azure, управляемый экземпляр SQL Azure, виртуальные машины SQL) и хранилище данных SQL Azure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Для управления (запросов, мониторинга и т. д.) базы данных необходим инструмент. Хотя ваши базы данных могут работать в облаке, в Windows или в [Linux](../linux/sql-server-linux-overview.md), средство не нужно запускать на той же платформе, что и база данных. 

Доступно множество инструментов для работы с базами данных, поэтому в этой статье приводятся описания и ссылки на некоторые из доступных инструментов по работе с базами данных SQL. Если вам нужна помощь в принятии решения об использовании нужного средства, см. раздел [какое средство использовать?](#which-tool-should-i-choose).

Для получения дополнительных сведений и для загрузки средства выберите ссылки в столбце инструмент в следующих таблицах. Сведения о скачивании SQL Server см. в разделе [Install SQL Server](../database-engine/install-windows/install-sql-server.md). 

## <a name="gui-tools-to-manage-databases"></a>Средства графического пользовательского интерфейса для управления базами данных  

Следующие средства предоставляют графический пользовательский интерфейс (GUI):

| Инструмент | Описание | Выполняется в |
|:--|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)]— Это бесплатное средство для управления базами данных в любом месте, где они выполняются. Этот предварительный выпуск предоставляет функции управления базами данных, в том числе Расширенный редактор Transact-SQL и настраиваемые аналитические сведения о рабочем состоянии баз данных. | **[!INCLUDE[name-sos](../includes/name-sos-short.md)] выполняется в Windows, macOS и Linux.**|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Используйте SQL Server Management Studio (SSMS) для запроса, проектирования и управления SQL Server, базой данных SQL Azure и хранилищем данных SQL Azure. | **SSMS работает на ОС Windows**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Преобразуйте Visual Studio в мощную среду разработки для SQL Server, базы данных SQL Azure и хранилища данных SQL Azure.| **SSDT работает в Windows**.|
| [Visual Studio Code](https://code.visualstudio.com/);| После установки Visual Studio Code установите [расширение MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) для разработки Microsoft SQL Server, базы данных SQL Azure и хранилища данных SQL.| **Visual Studio Code работает в Windows, macOS и Linux**.|


## <a name="command-line-tools-to-manage-databases"></a>Средства командной строки для управления базами данных

Ниже перечислены основные средства командной строки.

| Инструмент | Описание | Выполняется в |
|:--|:--|:--|
|[**mssql-cli (предварительная версия)** ](mssql-cli.md)|**MSSQL-CLI** — это интерактивное средство командной строки для запроса SQL Server. | Windows, macOS и Linux|
| [**sqlpackage**](sqlpackage.md) |**SqlPackage** — это программа командной строки, которая автоматизирует несколько задач разработки баз данных. версии SqlPackage macOS и Linux в настоящее время доступны в предварительной версии. | Windows, macOS и Linux|
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** предоставляет командлеты для работы с SQL| Windows, macOS и Linux|
| [**sqlcmd**](sqlcmd-utility.md) |Программа **sqlcmd** позволяет вводить в командной строке инструкции TRANSACT-SQL, системные процедуры и файлы скриптов. | Windows, macOS и Linux|
|[**bcp**](https://docs.microsoft.com/sql/tools/bcp-utility?view=sql-server-2014)|Служебная программа "**b**ulk **c**opy **p**rogram" (**bcp**) используется для массового копирования данных между экземпляром [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и файлом данных в указанном пользователем формате.|Windows, macOS и Linux|
|[**MSSQL-Scripter (Предварительная версия)** ](https://github.com/Microsoft/mssql-scripter)|**MSSQL-Scripter** — это многоплатформенный интерфейс командной строки для создания скриптов SQL Server баз данных|Windows, macOS и Linux|
|[**mssql-conf**](../linux/sql-server-linux-configure-mssql-conf.md)|**MSSQL-CONF** настраивает SQL Server, выполняющиеся в Linux.|Linux|



## <a name="which-tool-should-i-choose"></a>Какой инструмент следует выбрать?

- Вы хотите управлять SQL Server экземпляром или базой данных в облегченном редакторе в Windows, Linux или Mac? Выберите [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md)
- Вы хотите управлять SQL Server экземпляром или базой данных в Windows с полной поддержкой GUI? Выберите [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- Вы хотите создать или поддерживать код базы данных, включая проверку времени компиляции, рефакторинг и поддержку конструктора в Windows? Выберите [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- Вы хотите запросить SQL Server с помощью программы командной строки, в которой реализована технология IntelliSense, высокая степень освещения и многое другое? Выбор [MSSQL-CLI](mssql-cli.md)
- Вы хотите писать скрипты T-SQL в облегченном редакторе для Windows, Linux или Mac? Выберите [Visual Studio Code](https://code.visualstudio.com/) и [расширение MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)



## <a name="additional-tools"></a>Дополнительные средства

| Инструмент | Описание |
|:--|:--|
| [диспетчер конфигураций](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Используйте диспетчер конфигурации SQL Server для настройки служб SQL Server и настройки сетевого подключения. Configuration Manager работает в Windows|
| [Помощник по миграции SQL Server](../ssma/sql-server-migration-assistant.md) | Помощник по миграции SQL Server используется для автоматизации миграции баз данных в SQL Server из Microsoft Access, DB2, MySQL, Oracle и Sybase.|
| [Database Experimentation Assistant](../dea/database-experimentation-assistant-overview.md) | Используйте Database Experimentation Assistant, чтобы оценить целевую версию SQL для данной рабочей нагрузки. |
| [Распределенное воспроизведение](../tools/distributed-replay/install-distributed-replay-overview.md) | Используйте функцию распределенное воспроизведение, которая поможет оценить влияние будущих обновлений SQL Server. Кроме того, используйте распределенное воспроизведение, чтобы оценить влияние обновления оборудования и операционной системы, а также SQL Server настройку. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Служебная программа ssbdiagnose сообщает о проблемах Service Broker диалогов или настройке служб Service Broker. |

Если вы ищете дополнительные средства, которые не упоминаются на этой странице, см. раздел [программы командной строки SQL](command-prompt-utility-reference-database-engine.md).

