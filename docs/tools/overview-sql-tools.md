---
title: SQL средства и служебные программы для SQL Server, база данных Azure SQL и хранилище данных Azure SQL | Документация Майкрософт
ms.custom: ''
ms.date: 11/19/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 84cebceddc18ee3d288226ebd00bc86ea25ac926
ms.sourcegitcommit: eb1f3a2f5bc296f74545f17d20c6075003aa4c42
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190994"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>Средства и программы для SQL Server, база данных Azure SQL и хранилище данных Azure SQL SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Для управления (запросов, монитор, и т.д.) требуется инструмент базы данных. Хотя базы данных могут работать в облаке, на Windows или на [Linux](../linux/sql-server-linux-overview.md), ваше средство не должен выполняться на той же платформе, что и база данных. 

Существует множество инструменты для баз данных, поэтому в этой статье представлено описание и ссылки на некоторые из доступных средств работы с базами данных SQL. Если вам нужна помощь, решить, какое средство см [какие средства следует использовать?](#which-tool-should-i-choose).


## <a name="gui-tools-to-manage-databases"></a>Графические средства для управления базами данных  

Ниже приведены средства основного графического пользовательского интерфейса (GUI).

| Инструмент | Описание | Работает на |
|:--|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] — это бесплатные, облегченные средство для управления базами данных везде, где они выполняются. Эта предварительная версия предоставляет возможности управления базы данных, включая расширенного редактора Transact-SQL и настраиваемые ценные сведения о работоспособности баз данных. | **[!INCLUDE[name-sos](../includes/name-sos-short.md)] работает в Windows, macOS и Linux**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Используйте SQL Server Management Studio (SSMS) для запроса, проектирования и управления SQL Server, базы данных SQL Azure и хранилище данных SQL Azure. | **SSMS работает на ОС Windows**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Visual Studio можно Превратите в мощную среду разработки для SQL Server, базы данных SQL Azure и хранилище данных SQL Azure.| **SSDT работает в Windows**.|
| [Visual Studio Code](https://code.visualstudio.com/);| После установки Visual Studio Code, установить [расширение mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) по разработке Microsoft SQL Server, базы данных SQL Azure и хранилище данных SQL.| **Запускает Visual Studio Code в Windows, macOS и Linux**.|


## <a name="command-line-tools-to-manage-databases"></a>Средства командной строки для управления базами данных

Ниже приведены основные средства командной строки.

| Инструмент | Описание | Работает на |
|:--|:--|:--|
|[**mssql-cli (предварительная версия)**](mssql-cli.md)|**MSSQL-cli** — это интерактивное средство командной строки для выполнения запросов к SQL Server. | Windows, macOS и Linux|
| [**sqlpackage**](sqlpackage.md) |**sqlpackage** — это программа командной строки, которая позволяет автоматизировать некоторые задачи разработки базы данных. macOS и Linux, версиях sqlpackage сейчас доступны в предварительной версии. | Windows, macOS и Linux|
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** предоставляет командлеты для работы с SQL| Windows, macOS и Linux|
| [**sqlcmd**](sqlcmd-utility.md) |**sqlcmd** служебная программа позволяет вводить инструкции Transact-SQL, системные процедуры и файлы скриптов в командной строке. | Windows, macOS и Linux|
|[**bcp**](https://docs.microsoft.com/sql/tools/bcp-utility?view=sql-server-2014)|Служебная программа "**b**ulk **c**opy **p**rogram" (**bcp**) используется для массового копирования данных между экземпляром [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и файлом данных в указанном пользователем формате.|Windows, macOS и Linux|
|[**MSSQL-scripter (Предварительная версия)**](https://github.com/Microsoft/mssql-scripter)|**MSSQL-scripter** — это интерфейс командной строки для нескольких платформ для сценариев баз данных SQL Server|Windows, macOS и Linux|
|[**MSSQL-conf**](../linux/sql-server-linux-configure-mssql-conf.md)|**MSSQL-conf** настраивает SQL Server на Linux.|Linux|



## <a name="which-tool-should-i-choose"></a>Какое средство следует выбрать?

- Вы хотите управлять на экземпляре SQL Server или базу данных, в редакторе недоступно: в Windows, Linux или Mac? Выберите [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md)
- Вы хотите управлять на экземпляре SQL Server или базу данных в Windows с полной поддержкой графического пользовательского интерфейса? Выберите [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- Сделать нужно создать или настроить код базы данных, включая проверки во время компиляции, рефакторинга и конструктор, поддерживают на Windows? Выберите [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- Вы действительно хотите запросить SQL Server с помощью функции IntelliSense, синтаксис высокого освещения, средство командной строки и многое другое? Выберите [mssql-cli](mssql-cli.md)
- Вы хотите написать сценарии T-SQL в редакторе недоступно: в Windows, Linux или Mac? Выберите [Visual Studio Code](https://code.visualstudio.com/) и [расширение mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)



## <a name="additional-tools"></a>Дополнительные средства

| Инструмент | Описание |
|:--|:--|
| [Диспетчер конфигураций](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Используйте диспетчер конфигурации SQL Server для настройки служб SQL Server и настройках сетевого взаимодействия. Configuration Manager работает на Windows|
| [Помощник по миграции SQL Server](../ssma/sql-server-migration-assistant.md) | Помощник по миграции SQL Server используется для автоматизации миграции баз данных в SQL Server из Microsoft Access, DB2, MySQL, Oracle и Sybase.|
| [Database Experimentation Assistant](../dea/database-experimentation-assistant-overview.md) | Используйте помощник базы данных службы "Экспериментирование" для оценки целевую версию SQL для заданной рабочей нагрузки. |
| [Распределенное воспроизведение](../tools/distributed-replay/install-distributed-replay-overview.md) | Используйте компонента распределенного воспроизведения, которые помогут оценить влияние будущих обновлений SQL Server. Также можно используйте распределенного воспроизведения для оценки влияния оборудования и обновления операционной системы и настройке SQL Server. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Программа ssbdiagnose сообщает о проблемах в диалогах компонента Service Broker или в конфигурации служб компонента Service Broker. |

Если вы ищете дополнительные средства, не упомянутые на этой странице, см. в разделе [программы командной строки SQL](command-prompt-utility-reference-database-engine.md).

