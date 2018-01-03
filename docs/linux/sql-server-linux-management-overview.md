---
title: "Управление SQL Server для Linux | Документы Microsoft"
description: "В этом разделе содержатся ссылки на общие задачи управления и средства для SQL Server под управлением Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.custom: 
ms.workload: On Demand
ms.openlocfilehash: 0f775666ae0ba3e5bc9140e52ec2f532d6b92e0c
ms.sourcegitcommit: 73043fe1ac5d60b67e33b44053c0a7733b98bc3d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/23/2017
---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Выбрать правильное средство для управления SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Существует несколько способов управления 2017 г. SQL Server в Linux. Следующий раздел содержит краткий обзор средств управления и приемов с указателями на дополнительные ресурсы.

## <a name="mssql-conf"></a>MSSQL conf 
**Mssql conf** средство настраивает SQL Server в Linux. Дополнительные сведения см. в разделе [Настройка SQL Server в Linux с mssql conf](sql-server-linux-configure-mssql-conf.md).

## <a name="transact-sql"></a>Transact-SQL

Практически все, что можно сделать в клиентском средстве также можно с помощью инструкций Transact-SQL. SQL Server предоставляет [динамические административные представления (DMV)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) , запрос состояния и конфигурации SQL Server. Существуют также [команд Transact-SQL](https://msdn.microsoft.com/library/bb510741.aspx) для задачи управления базами данных. Эти команды запускаются в любое клиентское средство, которое поддерживает подключение к SQL Server и выполнение запросов Transact-SQL, например [sqlcmd](sql-server-linux-setup-tools.md) или [кода Visual Studio](sql-server-linux-develop-use-vscode.md).

## <a name="sql-server-operations-studio-preview"></a>SQL Server Operations Studio (Предварительная версия)

Новые операции Studio Microsoft SQL (Предварительная версия) — это средство кросс платформенных управления SQL Server. Дополнительные сведения см. в разделе [возможности Microsoft SQL Studio (Предварительная версия) для операций](../sql-operations-studio/what-is.md).

## <a name="sql-server-management-studio-on-windows"></a>SQL Server Management Studio в Windows

SQL Server Management Studio (SSMS) — это приложение Windows, который предоставляет графический пользовательский интерфейс для управления SQL Server. Несмотря на то, что она в настоящее время выполняется только в Windows, его можно использовать для удаленного подключения к экземпляру SQL Server для Linux. Дополнительные сведения об использовании SSMS для управления SQL Server см. в разделе [используйте SSMS для управления SQL Server в Linux](sql-server-linux-manage-ssms.md).

## <a name="mssql-cli-preview"></a>MSSQL-cli (Предварительная версия)

Корпорация Майкрософт выпустила новое средство поддержки скриптов в кросс платформенных для SQL Server, [mssql cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/). Это средство находится в режиме предварительного просмотра.

## <a name="powershell"></a>PowerShell

PowerShell предоставляет среду с широкими возможностями командной строки для управления SQL Server в Linux. Дополнительные сведения см. в разделе [управления SQL Server в Linux с помощью PowerShell](sql-server-linux-manage-powershell.md).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о SQL Server в Linux см. в разделе [SQL Server в Linux](sql-server-linux-overview.md).
