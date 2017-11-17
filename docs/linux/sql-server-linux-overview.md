---
title: "Общие сведения о SQL Server для Linux | Документы Microsoft"
description: "В этом разделе описывается, как SQL Server работает на ОС Linux и предоставляет сведения о том, как получить дополнительные сведения."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 48e2d1ae54100f7ea83bdd677bf4a98859825b67
ms.contentlocale: ru-ru
ms.lasthandoff: 10/05/2017

---
# <a name="sql-server-on-linux"></a>SQL Server в Linux:

SQL Server 2017 теперь работает на платформе Linux. Это же движок SQL Server, с аналогичными возможностями и службами, в независимости от вашей операционной системы.

## <a name="install"></a>Установка

Чтобы приступить к работе, необходимо установить SQL Server на Linux с помощью одной из следующих инструкций:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker сам по себе работает на разных платформах, что означает, что образ Docker можно запускать в Linux, Mac и Windows.

## <a name="connect"></a>Подключение

После установки вы можете подключититься к экземпляру SQL Server локально или удаленно с помощью различных средств и драйверов. Вы можете использовать утилиту командной строки [sqlcmd](sql-server-linux-setup-tools.md). Ниже также приведены ссылки на другие инструменты:

| Инструмент | Учебник |
|-----|-----|
| Visual Studio (VS код) | [Использование кода VS с SQL Server на Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Использование SSMS в Windows для подключения к SQL Server на Linux](sql-server-linux-develop-use-ssms.md) |
| SQL Server Data Tools (SSDT) | [Использование средств SSDT с SQL Server на Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Изучение

В SQL Server 2017 используется один и тот же движок баз данных на всех поддерживаемых платформах включая Linux. Поэтому многие существующие функции и возможности работают так же и в Linux. В этой части документации представлены некоторые из этих функций с точки зрения Linux, а также некоторые специфические особенности работы на этой платформе.

Если вы уже знакомы с SQL Server, то можете просмотреть общие рекомендации и список известных проблем в [Release notes](sql-server-linux-release-notes.md). Также вгляните [что нового в SQL Server на Linux](sql-server-linux-whats-new.md) и [что нового в SQL Server 2017 в общем](../sql-server/what-s-new-in-sql-server-2017.md).

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](./media/general/info_tip.png) Общение с командой разработчиков SQL Server

- [DBA Stack Exchange](https://dba.stackexchange.com/questions/tagged/sql-server): задать вопросы по администрированию баз данных
- [Stack Overflow](http://stackoverflow.com/questions/tagged/sql-server): вопросы разработки
- [Форумы MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): задавайте технические вопросы
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): ошибки и предложения
- [Reddit](https://www.reddit.com/r/SQLServer/): обсудить SQL Server

