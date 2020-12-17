---
title: mssql-cli
description: mssql-cli представляет собой интерактивное средство запроса для командной строки в SQL Server, которое может работать в Windows, macOS и Linux.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, sstein, maghan
ms.custom: tools|mssql-cli
ms.date: 02/22/2018
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017
ms.openlocfilehash: 345d188106877f5f5aa6740c7e4db7c0c0511bfb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471785"
---
# <a name="mssql-cli-command-line-query-tool-for-sql-server-preview"></a>Средство создания запросов из командной строки mssql-cli для SQL Server (предварительная версия)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

mssql-cli представляет собой интерактивное средство создания запросов к SQL Server из командной строки, которое может работать в Windows, macOS и Linux.

## <a name="install-mssql-cli"></a>Установка mssql-cli

Подробные инструкции по установке см. в [руководстве по установке](https://github.com/dbcli/mssql-cli/tree/master/doc/installation). Ниже приведены наиболее распространенные сценарии установки.

### <a name="windows-and-macos-installation"></a>Установка в ОС Windows и macOS

Для установки mssql-cli в ОС Windows и macOS используется `pip`.

```$ pip install mssql-cli```

Более подробные инструкции см. в [руководстве по установке](https://github.com/dbcli/mssql-cli/tree/master/doc/installation).

### <a name="linux-installation"></a>Установка в Linux

После регистрации репозитория Майкрософт средство mssql-cli можно установить и обновить с помощью диспетчеров пакетов в нескольких дистрибутивах Linux.

Следующий пример применим к Ubuntu 18.04 (Bionic), дополнительные сведения и примеры для других дистрибутивов см. в [руководстве по установке](https://github.com/dbcli/mssql-cli/tree/master/doc/installation).

```
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo apt-add-repository https://packages.microsoft.com/ubuntu/18.04/prod

# Update the list of products
sudo apt-get update

# Install mssql-cli
sudo apt-get install mssql-cli

# Install missing dependencies
sudo apt-get install -f
```

## <a name="mssql-cli-documentation"></a>Документация по mssql-cli

Документация по mssql-cli находится в репозитории [mssql-cli GitHub](https://github.com/dbcli/mssql-cli).

- [Главная страница и файл сведений](https://github.com/dbcli/mssql-cli)
- [Руководство по установке](https://github.com/dbcli/mssql-cli/tree/master/doc/installation)
- [Рекомендации по использованию](https://github.com/dbcli/mssql-cli/blob/master/doc/usage_guide.md)

Дополнительная документация находится в папке [doc](https://github.com/dbcli/mssql-cli/tree/master/doc).
