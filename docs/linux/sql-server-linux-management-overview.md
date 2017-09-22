---
title: "Управление SQL Server для Linux | Документы Microsoft"
description: "В этом разделе содержатся ссылки на общие задачи управления и средства для SQL Server под управлением Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 5f7c0f61cf9f441c56529ddaaddc96a0c318ce59
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Выбрать правильное средство для управления SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Существует несколько способов управления RC2 2017 г. SQL Server в Linux. Следующий раздел выполнять обзор различных управления инструментов и методов с указателями на дополнительные ресурсы.

## <a name="mssql-conf"></a>MSSQL conf 
**Mssql conf** средство настраивает SQL Server в Linux. Дополнительные сведения см. в разделе [Настройка SQL Server в Linux с mssql conf](sql-server-linux-configure-mssql-conf.md).

## <a name="transact-sql"></a>Transact-SQL

Практически все, что можно сделать в клиентском средстве также можно с помощью инструкций Transact-SQL. SQL Server предоставляет [динамические административные представления (DMV)](/sql-docs/docs/relational-databases/system-dynamic-management-views/system-dynamic-management-views) , запрос состояния и конфигурации SQL Server. Существуют также [команд Transact-SQL](https://msdn.microsoft.com/library/bb510741.aspx) для задачи управления базами данных. Эти команды запускаются в любое клиентское средство, которое поддерживает подключение к SQL Server и выполнение запросов Transact-SQL. Примеры включают [sqlcmd](sql-server-linux-setup-tools.md), [кода Visual Studio](sql-server-linux-develop-use-vscode.md), и [SQL Server Management Studio](sql-server-linux-manage-ssms.md).

## <a name="sql-server-management-studio-on-windows"></a>SQL Server Management Studio в Windows

SQL Server Management Studio (SSMS) — это приложение Windows, который предоставляет графический пользовательский интерфейс для управления SQL Server. Несмотря на то, что она в настоящее время выполняется только в Windows, его можно использовать для удаленного подключения к экземпляру SQL Server для Linux. Дополнительные сведения об использовании SSMS для управления SQL Server см. в разделе [используйте SSMS для управления SQL Server в Linux](sql-server-linux-manage-ssms.md).

## <a name="powershell"></a>PowerShell

PowerShell предоставляет среду с широкими возможностями командной строки для управления SQL Server в Linux. Дополнительные сведения см. в разделе [управления SQL Server в Linux с помощью PowerShell](sql-server-linux-manage-powershell.md).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о SQL Server в Linux см. в разделе [SQL Server в Linux](sql-server-linux-overview.md).
