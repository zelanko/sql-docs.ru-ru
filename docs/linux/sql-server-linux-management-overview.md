---
title: Управление SQL Server в Linux | Документация Майкрософт
description: В этой статье ссылки на общие задачи управления и средства для SQL Server на платформе Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.custom: sql-linux
ms.openlocfilehash: e3b76a386598b7439d9cb2ffbad738d86b1b9183
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788252"
---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Выбор подходящего средства для управления SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Существует несколько способов управления SQL Server в Linux. Следующий раздел содержит краткий обзор управления различных инструментов и методов с указателями на дополнительные ресурсы.

## <a name="mssql-conf"></a>MSSQL-conf 

**Mssql-conf** средство настраивает SQL Server в Linux. Дополнительные сведения см. в разделе [Настройка SQL Server в Linux с помощью mssql-conf](sql-server-linux-configure-mssql-conf.md).

## <a name="transact-sql"></a>Transact-SQL

Почти все, что можно сделать в клиентском средстве также может быть выполнено с помощью инструкций Transact-SQL. SQL Server предоставляет [динамические административные представления (DMV)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) , запрос состояния и конфигурации SQL Server. Существуют также [команд Transact-SQL](../t-sql/language-reference.md) для задач управления базами данных. Эти команды можно запустить в любой клиентский инструмент, который поддерживает подключение к SQL Server и выполнение запросов Transact-SQL, например [sqlcmd](sql-server-linux-setup-tools.md) или [Visual Studio Code](sql-server-linux-develop-use-vscode.md).

## <a name="azure-data-studio-preview"></a>Azure Data Studio (Предварительная версия)

Новый Studio данных Azure (Предварительная версия) — это кросс платформенного средства управления SQL Server. Дополнительные сведения см. в разделе [Studio данных Azure (Предварительная версия)](../azure-data-studio/what-is.md).

## <a name="sql-server-management-studio-on-windows"></a>SQL Server Management Studio в Windows

SQL Server Management Studio (SSMS) — это приложение Windows, который предоставляет графический пользовательский интерфейс для управления SQL Server. В настоящее время работает только в Windows, его можно использовать для удаленного подключения к экземплярам SQL Server для Linux. Дополнительные сведения об использовании SSMS для управления SQL Server, см. в разделе [используйте SSMS для управления SQL Server в Linux](sql-server-linux-manage-ssms.md).

## <a name="mssql-cli-preview"></a>MSSQL-cli (Предварительная версия)

Корпорация Майкрософт выпустила новый кросс платформенного средства создания скриптов для SQL Server, [mssql-cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/). Это средство находится в предварительной версии.

## <a name="powershell"></a>PowerShell

PowerShell предоставляет среду с широкими возможностями командной строки для управления SQL Server в Linux. Дополнительные сведения см. в разделе [управления SQL Server в Linux с помощью PowerShell](sql-server-linux-manage-powershell.md).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о SQL Server в Linux, см. в разделе [SQL Server в Linux](sql-server-linux-overview.md).
