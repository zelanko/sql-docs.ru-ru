---
title: Обзор SQL Server в Linux
description: В этой статье описывается, как SQL Server выполняется в системе Linux и предоставляет сведения о том, как для получения дополнительных сведений.
author: VanMSFT
ms.author: vanto
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.openlocfilehash: e3bd50cba4bcab81e7dcf00db9394704c5486160
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68105460"
---
# <a name="sql-server-on-linux"></a>SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: moniker range="= sql-server-2017 || = sqlallproducts-allversions"
Начиная с SQL Server 2017, SQL Server выполняется в системе Linux. Это такое же ядро СУБД SQL Server, много подобных возможностей и служб независимо от операционной системы.
::: moniker-end

::: moniker range=">= sql-server-ver15 || >= sql-server-linux-ver15"
Предварительная версия SQL Server 2019 выполняется в системе Linux. Это такое же ядро СУБД SQL Server, много подобных возможностей и служб независимо от операционной системы. Чтобы узнать больше об этом выпуске, см. в разделе [новые возможности в предварительной версии SQL Server 2019 для Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sql-server-on-linux).
::: moniker-end

::: moniker range="= sql-server-2017"
> [!TIP]
> [Предварительная версия SQL Server 2019](sql-server-linux-overview.md?view=sql-server-ver15) была выпущена! Новые возможности для Linux в последнем выпуске см. в статье [новые возможности в предварительной версии SQL Server 2019 для Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).
::: moniker-end

::: moniker range="= sql-server-linux-2017"
> [!TIP]
> [Предварительная версия SQL Server 2019](sql-server-linux-overview.md?view=sql-server-linux-ver15) была выпущена! Новые возможности для Linux в последнем выпуске см. в статье [новые возможности в предварительной версии SQL Server 2019 для Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-linux-ver15#sql-server-on-linux).
::: moniker-end

::: moniker range="= sqlallproducts-allversions"
> [!TIP]
> Предварительная версия SQL Server 2019 была выпущена! Новые возможности для Linux в последнем выпуске см. в статье [новые возможности в предварительной версии SQL Server 2019 для Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sql-server-on-linux).
::: moniker-end

## <a name="install"></a>Установка

Чтобы начать работу, установите SQL Server в Linux с помощью одного из следующих кратких руководств:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустить в Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

> [!NOTE]
> Docker сам по себе работает на разных платформах, что означает, что образ Docker можно запускать в Linux, Mac и Windows.

## <a name="connect"></a>Подключение

После установки подключитесь к экземпляру SQL Server на компьютере Linux. Можно подключить локально или удаленно и разнообразные средства и драйверы. Краткие руководства демонстрируется использование [sqlcmd](sql-server-linux-setup-tools.md) средство командной строки. Ниже также приведены ссылки на другие инструменты:

| Инструмент | Учебник |
|-----|-----|
| Visual Studio Code (VS Code) | [Использование VS Code с SQL Server в Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Использование SSMS в Windows для подключения к SQL Server на Linux](sql-server-linux-manage-ssms.md) |
| SQL Server Data Tools (SSDT) | [Использование средств SSDT с SQL Server в Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Изучение

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В SQL Server 2017 используется одно и то же ядро СУБД на всех поддерживаемых платформах, включая Linux. Таким образом многие существующие функции и возможности работают одинаково в Linux. В этой части документации предоставляет некоторые из этих функций с точки зрения Linux. Он также вызывает областей, которые имеют уникальные требования в Linux.

Если вы уже знакомы с SQL Server, то можете просмотреть общие рекомендации и список известных проблем в [заметках о выпуске](sql-server-linux-release-notes.md) Кроме того, взгляните, [что нового в SQL Server на Linux](sql-server-linux-whats-new.md) и [что нового в SQL Server 2017 в общем](../sql-server/what-s-new-in-sql-server-2017.md).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15"

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] на всех поддерживаемых платформах, включая Linux, имеет тот же базовый механизм базы данных. Таким образом многие существующие функции и возможности работают одинаково в Linux. В этой части документации предоставляет некоторые из этих функций с точки зрения Linux. Он также вызывает областей, которые имеют уникальные требования в Linux.

Если вы уже знакомы с SQL Server в Linux, просмотрите [заметки о выпуске](sql-server-linux-release-notes-2019.md) Общие рекомендации и известные проблемы в этом выпуске. Затем рассмотрим [новые возможности предварительной версии SQL Server 2019 в Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15).

::: moniker-end

<!--SQL Server All Versions-->
::: moniker range="=sqlallproducts-allversions"

SQL Server 2017 и [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] имеют один и тот же базовый механизм базы данных на всех поддерживаемых платформах, включая Linux. Таким образом многие существующие функции и возможности работают одинаково в Linux. В этой части документации предоставляет некоторые из этих функций с точки зрения Linux. Он также вызывает областей, которые имеют уникальные требования в Linux.

Если вы уже знакомы с SQL Server в Linux, заметки о выпуске:

- [Заметки о выпуске для SQL Server 2017](sql-server-linux-release-notes.md)
- [Заметки о выпуске предварительной версии SQL Server 2019](sql-server-linux-release-notes-2019.md)

Затем рассмотрим новые возможности:

- [Новые возможности SQL Server 2017](sql-server-linux-whats-new.md)
- [Новые возможности предварительной версии SQL Server 2019 в Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sql-server-on-linux)

::: moniker-end

> [!TIP]
> Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](sql-server-linux-faq.md).

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
