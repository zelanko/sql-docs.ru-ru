---
title: "Разработка приложений для SQL Server для Linux | Документы Microsoft"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 7fcd3350796d88d02011f0d45e666851d69cfd78
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>Как приступить к разработке приложений для SQL Server в Linux

Можно создавать приложения, подключения и использования RC2 2017 г. SQL Server в Linux из различных языков программирования, например C#, Java, Node.js, PHP, Python, Ruby и C++. Можно также использовать популярных веб-платформ и платформ объекта реляционного сопоставления (ORM).

> [!TIP]
> Эти же параметры разработки также обеспечивают целевого SQL Server на других платформах. Приложение можно настроить SQL Server, работающий локально или в облаке, в Linux, Windows или Docker на macOS. Или можно выбрать целевую базу данных SQL Azure и хранилище данных SQL Azure.

## <a name="try-the-tutorials"></a>Использовать учебники

Чтобы начать работу и создание приложений с помощью SQL Server рекомендуется испытать самостоятельно.

- Перейдите к [руководства по началу работы](http://aka.ms/sqldev).
- Выберите язык и разработки платформу.
- Попробуйте использовать примеры кода.

> [!TIP]
> Если вы хотите разрабатывать приложения для RC2 2017 г. SQL Server на Docker, взгляните на **macOS** учебники.

## <a name="create-new-applications"></a>Создание нового приложения

Если вы создаете новое приложение, взгляните на список [библиотек подключений](sql-server-linux-develop-connectivity-libraries.md) сводку соединителей и наиболее популярных платформ, доступные для различных языков программирования.

## <a name="use-existing-applications"></a>Использовать существующие приложения

При наличии существующей базы данных приложения можно просто изменить строку соединения целевой RC2 2017 г. SQL Server в Linux. Убедитесь в том прочитать о [известные проблемы](sql-server-linux-release-notes.md) в RC2 2017 г. SQL Server в Linux.

## <a name="use-existing-sql-tools-on-windows-with-sql-server-on-linux"></a>Используйте существующие средства SQL в Windows с помощью SQL Server в Linux

Средства, которые в данный момент выполняются на Windows, таких как среда SSMS, SSDT и PowerShell, также работают с RC2 2017 г. SQL Server в Linux. Несмотря на то, что они работают не под управлением изначально в Linux, вы можете управлять удаленным экземплярам SQL Server в Linux. 

См. Дополнительные сведения в следующих разделах:

- [SQL Server Management Studio (SSMS)](sql-server-linux-develop-use-ssms.md)
- [SQL Server Data Tools (SSDT)](sql-server-linux-develop-use-ssdt.md)
- [SQL PowerShell](sql-server-linux-manage-powershell.md)

> [!Note] 
> Убедитесь, что вы используете последние версии этих средств для получения наилучших результатов.

## <a name="use-new-sql-tools-for-linux"></a>Использовать новое средство SQL для Linux

Вы можете использовать новый [mssql расширения](https://aka.ms/mssql-marketplace) для [кода Visual Studio](https://code.visualstudio.com) на macOS, Windows и Linux. Пошаговое руководство см. в следующем учебнике:

- [Используйте Visual Studio код](sql-server-linux-develop-use-vscode.md)

Можно также использовать новые средства командной строки, которые являются собственными для Linux. Эти средства включают следующие:

- [программа sqlcmd](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [MSSQL conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе, установка SQL Server в Linux с помощью одного из следующих учебников краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)

