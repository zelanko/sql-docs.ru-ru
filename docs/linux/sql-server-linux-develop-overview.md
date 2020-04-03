---
title: Разработка приложений для SQL Server на Linux
description: Вы можете создавать приложения, подключающиеся и использующие SQL Server на Linux, на разных языках программирования и популярных веб-платформах.
author: VanMSFT
ms.author: vanto
ms.date: 11/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.openlocfilehash: ad0b4de881afe1cf30f865540ddff692d1415d9c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80216784"
---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>Как приступить к разработке приложений для SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Вы можете создавать приложения, подключающиеся и использующие SQL Server на Linux, на разных языках программирования, включая C#, Java, Node.js, PHP, Python, Ruby и C++. Кроме того, можно использовать популярные веб-платформы и платформы ORM.

> [!VIDEO https://channel9.msdn.com/events/Connect/2017/T153/player]

> [!TIP]
> С помощью этих же средств можно вести разработку для SQL Server на других платформах. Приложения могут быть предназначены для SQL Server в локальной среде или облаке, в Linux, Windows или Docker в macOS. Кроме того, можно вести разработку для базы данных SQL Azure и Хранилища данных SQL Azure.

## <a name="try-the-tutorials"></a>Работа с учебниками

Учиться создавать приложения для SQL Server лучше всего на собственном опыте.

- Перейдите к [руководствам по началу работы](https://aka.ms/sqldev).
- Выберите язык и платформу разработки.
- Воспользуйтесь примерами кода.

> [!TIP]
> Если вы хотите разрабатывать приложения для SQL Server в Docker, обратитесь к руководствам для **macOS**.

## <a name="create-new-applications"></a>Создание приложений

Если вы создаете приложение, просмотрите список [библиотек подключения](sql-server-linux-develop-connectivity-libraries.md), чтобы получить общие сведения о соединителях и популярных платформах, доступных для различных языков программирования.

## <a name="use-existing-applications"></a>Использование существующих приложений

Если у вас уже есть приложение базы данных, можно просто изменить его строку подключения, чтобы подключить его к SQL Server на Linux. Ознакомьтесь с [известными проблемами](sql-server-linux-release-notes.md) SQL Server на Linux.

## <a name="use-existing-sql-tools-on-windows-with-sql-server-on-linux"></a>Работа с SQL Server на Linux с помощью средств SQL для Windows

Существующие средства для Windows, такие как SSMS, SSDT и PowerShell, также работают с SQL Server на Linux. Хотя их нельзя запускать в Linux, они позволяют управлять удаленными экземплярами SQL Server на Linux. 

Дополнительные сведения см. в следующих статьях:

- [SQL Server Management Studio (SSMS)](sql-server-linux-manage-ssms.md)
- [SQL Server Data Tools (SSDT)](sql-server-linux-develop-use-ssdt.md)
- [SQL PowerShell](sql-server-linux-manage-powershell.md)

> [!Note]
> Для оптимальной работы используйте последние версии этих средств.

## <a name="use-new-sql-tools-for-linux"></a>Использование новых средств SQL для Linux

Вы можете использовать новое [расширение mssql](https://aka.ms/mssql-marketplace) для [Visual Studio Code](https://code.visualstudio.com) в Linux, macOS и Windows. Пошаговые инструкции см. в следующем руководстве:

- [Использование Visual Studio Code](sql-server-linux-develop-use-vscode.md)

Кроме того, можно использовать новые программы командной строки, предназначенные для Linux. К ним относятся следующие программы:

- [sqlcmd](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [mssql-conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>Дальнейшие действия

Чтобы начать работу, установите SQL Server на Linux, используя любое из следующих кратких руководств:

- [Установка в Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка в SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запуск в Docker](quickstart-install-connect-ubuntu.md)
