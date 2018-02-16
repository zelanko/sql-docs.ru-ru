---
title: "Общие сведения о SQL Server для Linux | Документы Microsoft"
description: "Эта статья описывает, как SQL Server работает на ОС Linux и предоставляет сведения о том, как для получения дополнительных сведений."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/21/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.workload: Active
ms.openlocfilehash: d0047c61b5b02ad392da9e4b88deedc2033d070a
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="sql-server-on-linux"></a>SQL Server в Linux:

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server 2017 теперь работает на платформе Linux. Это то же ядро СУБД SQL Server со многими аналогичными возможностями и службами, не зависящими от вашей операционной системы.

## <a name="install"></a>Установка

Чтобы приступить к работе, установите SQL Server в Linux с помощью одного из следующих краткие руководства:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker сам по себе работает на разных платформах, что означает, что образ Docker можно запускать в Linux, Mac и Windows.

## <a name="connect"></a>Подключить

После установки подключения к экземпляру SQL Server на компьютере Linux. Можно подключить локально или удаленно и с помощью различных средств и драйверов. Примеры использования демонстрируют использование [sqlcmd](sql-server-linux-setup-tools.md) средство командной строки. Ниже приведены другие средства:

| Инструмент | Учебник |
|-----|-----|
| Visual Studio (VS код) | [Использование кода VS с SQL Server в Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Использование SSMS в Windows для подключения к SQL Server на Linux](sql-server-linux-develop-use-ssms.md) |
| SQL Server Data Tools (SSDT) | [Использование средств SSDT с SQL Server в Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Изучение

2017 г. SQL Server имеет тот же базовый механизм базы данных на всех поддерживаемых платформах, включая Linux. Поэтому многие существующие функции и возможности работают так же, как в Linux. В этой части документации предоставляет некоторые из этих функций с точки зрения Linux. Он также вызывает областей, которые обладают уникальными требованиями в Linux.

Если вы уже знакомы с SQL Server, то можете просмотреть общие рекомендации и список известных проблем в [заметках о выпуске](sql-server-linux-release-notes.md) Кроме того, взгляните, [что нового в SQL Server на Linux](sql-server-linux-whats-new.md) и [что нового в SQL Server 2017 в общем](../sql-server/what-s-new-in-sql-server-2017.md). Ответы на часто задаваемые вопросы см. в разделе [SQL Server в Linux часто задаваемые вопросы о](sql-server-linux-faq.md).

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](./media/general/info_tip.png) Общение с командой разработчиков SQL Server

- [DBA Stack Exchange](https://dba.stackexchange.com/questions/tagged/sql-server): задать вопросы по администрированию баз данных
- [Stack Overflow](http://stackoverflow.com/questions/tagged/sql-server): вопросы разработки
- [Форумы MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): задавайте технические вопросы
- [Отправить отзыв о](https://feedback.azure.com/forums/908035-sql-server): ошибки и запрос функции отчетов
- [Reddit](https://www.reddit.com/r/SQLServer/): обсудить SQL Server
