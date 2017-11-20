---
title: "Общие сведения о SQL Server для Linux | Документы Microsoft"
description: "В этом разделе описывается, как SQL Server работает на ОС Linux и предоставляет сведения о том, как получить дополнительные сведения."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
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

SQL Server 2017 г. теперь работает на платформе Linux. Это же SQL Server database engine, с многие аналогичные функции и службы, независимо от операционной системы.

## <a name="install"></a>Установить

Чтобы приступить к работе, установка SQL Server в Linux с помощью одного из следующих учебников краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker сам выполняется на нескольких платформах, что означает, что образ Docker можно запускать в Linux, Mac и Windows.

## <a name="connect"></a>Connect

После установки подключения к экземпляру SQL Server на компьютере Linux. Можно подключить локально или удаленно и с помощью различных средств и драйверов. Быстрый запуск учебниках показано, как использовать [sqlcmd](sql-server-linux-setup-tools.md) средство командной строки. Ниже приведены другие средства:

| Инструмент | Учебник |
|-----|-----|
| Visual Studio (VS код) | [Использование кода VS с SQL Server в Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Используйте SSMS в Windows для подключения к SQL Server в Linux](sql-server-linux-develop-use-ssms.md) |
| SQL Server Data Tools (SSDT) | [Использование средств SSDT с SQL Server в Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Просмотр

2017 г. SQL Server имеет тот же базовый механизм базы данных на всех поддерживаемых платформах, включая Linux. Поэтому многие существующие функции и возможности работают так же, как в Linux. В этой части документации предоставляет некоторые из этих функций с точки зрения Linux. Он также вызывает областей, которые обладают уникальными требованиями в Linux.

Если вы уже знакомы с SQL Server, просмотрите [заметки о выпуске](sql-server-linux-release-notes.md) Общие рекомендации и известные проблемы в этом выпуске. Посмотрите на [новые для SQL Server в Linux](sql-server-linux-whats-new.md) и [новые для SQL Server 2017 г. общей](../sql-server/what-s-new-in-sql-server-2017.md).

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](./media/general/info_tip.png) Общение с командой разработчиков SQL Server

- [Администратор базы данных Exchange стека](https://dba.stackexchange.com/questions/tagged/sql-server): задать вопросы администрирования базы данных
- [Переполнение стека](http://stackoverflow.com/questions/tagged/sql-server): вопросы разработки
- [Форумы MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): задавайте технические вопросы
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): ошибки и запрос функции отчетов
- [Reddit](https://www.reddit.com/r/SQLServer/): обсудить SQL Server

