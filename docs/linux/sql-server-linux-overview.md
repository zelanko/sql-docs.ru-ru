---
title: Обзор SQL Server в Linux | Документация Майкрософт
description: В этой статье описывается, как SQL Server выполняется в системе Linux и предоставляет сведения о том, как для получения дополнительных сведений.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 06/20/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.openlocfilehash: 7327b336019cc2a3cf0244e1c6cd839f53042843
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082446"
---
# <a name="sql-server-on-linux"></a>SQL Server в Linux:

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server 2017 теперь работает на платформе Linux. Это то же ядро СУБД SQL Server со многими аналогичными возможностями и службами, не зависящими от вашей операционной системы.

## <a name="install"></a>Установка

Чтобы начать работу, установите SQL Server в Linux с помощью одного из следующих кратких руководств:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустить в Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

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

В SQL Server 2017 используется одно и то же ядро СУБД на всех поддерживаемых платформах, включая Linux. Поэтому многие существующие функции и возможности работают так же и в Linux.  В этой части документации предоставляет некоторые из этих функций с точки зрения Linux. Он также вызывает областей, которые имеют уникальные требования в Linux.

Если вы уже знакомы с SQL Server, то можете просмотреть общие рекомендации и список известных проблем в [заметках о выпуске](sql-server-linux-release-notes.md) Кроме того, взгляните, [что нового в SQL Server на Linux](sql-server-linux-whats-new.md) и [что нового в SQL Server 2017 в общем](../sql-server/what-s-new-in-sql-server-2017.md). 

> [!TIP]
> Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](sql-server-linux-faq.md).

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]