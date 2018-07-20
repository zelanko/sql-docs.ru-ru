---
title: При разработке приложений для SQL Server в Linux | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.custom: sql-linux
ms.suite: sql
ms.technology: linux
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.openlocfilehash: 317c2ea2064f7ffc286671a8fff7eef2f8149ee7
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084927"
---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>Как приступить к разработке приложений для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Можно создавать приложения, подключения и использования SQL Server 2017 на платформе Linux из различных языков программирования, например C#, Java, Node.js, PHP, Python, Ruby и C++. Можно также использовать популярные веб-платформ и платформ объектно-реляционного сопоставления (ORM).

> [!VIDEO https://channel9.msdn.com/events/Connect/2017/T153/player]

> [!TIP]
> Эти же параметры разработки также позволяют осуществлять целевой SQL Server на других платформах. Приложение можно настроить SQL Server, работающий в локальной или в облаке, в Linux, Windows или Docker в macOS. Или вы можете ориентироваться в базе данных SQL Azure и хранилище данных SQL Azure.

## <a name="try-the-tutorials"></a>Ознакомиться с учебниками

Лучший способ приступить к работе и создание приложений с помощью SQL Server находится в том, чтобы опробовать его самостоятельно.

- Перейдите к [руководства по началу работы](http://aka.ms/sqldev).
- Выберите платформу разработки и языка.
- Испытайте образцы кода.

> [!TIP]
> Если вы хотите разрабатывать для SQL Server 2017 в Docker, взгляните на **macOS** учебники.

## <a name="create-new-applications"></a>Создание новых приложений

Если вы создаете новое приложение, взгляните на список [библиотек подключений](sql-server-linux-develop-connectivity-libraries.md) сводные сведения о соединителях и популярных платформ, доступные для различных языков программирования.

## <a name="use-existing-applications"></a>Использовать существующие приложения

Если существующее приложение базы данных, можно просто изменить строку соединения для целевого SQL Server 2017 в Linux. Убедитесь в том прочитать о [известные проблемы](sql-server-linux-release-notes.md) в SQL Server 2017 в Linux.

## <a name="use-existing-sql-tools-on-windows-with-sql-server-on-linux"></a>Используйте существующие средства SQL в Windows с помощью SQL Server в Linux

Средства, которые в настоящее время запущены на Windows, таких как среда SSMS, SSDT и PowerShell, также работать с SQL Server 2017 в Linux. Несмотря на то, что они не выполняются в собственном коде в Linux, вы можете по-прежнему управлять удаленным экземплярам SQL Server в Linux. 

См. Дополнительные сведения в следующих разделах:

- [SQL Server Management Studio (SSMS)](sql-server-linux-manage-ssms.md)
- [SQL Server Data Tools (SSDT)](sql-server-linux-develop-use-ssdt.md)
- [SQL PowerShell](sql-server-linux-manage-powershell.md)

> [!Note]
> Убедитесь, что вы используете последние версии этих средств для получения наилучших результатов.

## <a name="use-new-sql-tools-for-linux"></a>Использовать новое средство SQL для Linux

Вы можете использовать новый [расширение mssql](https://aka.ms/mssql-marketplace) для [Visual Studio Code](https://code.visualstudio.com) в Linux, macOS и Windows. Пошаговое руководство см. в следующем руководстве:

- [Использование Visual Studio Code](sql-server-linux-develop-use-vscode.md)

Можно также использовать новые средства командной строки, являющиеся собственными для Linux. Эти средства включают следующие:

- [sqlcmd](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [mssql-conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>Следующие шаги

Чтобы начать работу, установите SQL Server в Linux с помощью одного из следующих кратких руководств:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустить в Docker](quickstart-install-connect-ubuntu.md)
