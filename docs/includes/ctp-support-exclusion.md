---
ms.openlocfilehash: ffd608faf64818a7acd9e38d9c502f575be6716a
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653031"
---
## <a name="enabled-deployment-scenarios"></a>Поддерживаемые сценарии развертывания

Релиз-кандидат (RC) SQL Server 2019 поддерживает следующие сценарии:

- Параллельная установка. Экземпляры SQL Server 2019 RC можно устанавливать с экземплярами SQL Server версий с 2012 по 2017 либо другими экземплярами SQL Server 2019 CTP 3.0 или более поздней версии.
   >[!NOTE]
   >Хотя параллельная установка вместе с версиями SQL Server 2008 и 2008 R2 не запрещена, нет таких версий операционной системы Windows, которые бы поддерживали как эти версии SQL Server, так и SQL Server 2019.
- Обновление на месте. Вы можете обновить экземпляры SQL Server версий с 2012 по 2017, а также экземпляры SQL Server CTP 3.0 до экземпляров SQL Server 2019 RC. Обновление с версий CTP SQL Server 2019 ниже версии 3.0 не поддерживается. Необходимо выполнить новую установку.
   >[!NOTE]
   >Хотя обновление на месте с версий SQL Server 2008 и 2008 R2 не запрещено, нет таких версий операционной системы Windows, которые бы поддерживали как эти версии SQL Server, так и SQL Server 2019.

## <a name="support"></a>Поддержка

SQL Server 2019 RC — это предварительная версия. Она не поддерживается официально в рабочих средах. Участники [программы для ранних последователей SQL](http://aka.ms/sqleap) могут заключить специальное соглашение, чтобы использовать SQL Server 2019 RC по согласованию с корпорацией Майкрософт.

Ограниченную поддержку для клиентов, не являющихся участниками программы для ранних последователей, можно найти в следующих ресурсах:

- Форумы
  - [Начало работы с SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted).
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [Документация по SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- Или опубликуйте твит [@SQLServer](https://twitter.com/SQLServer) с [#sqlhelp](https://twitter.com/search?q=%23sqlhelp).

**Попробуйте [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

- [![Скачайте из Центра оценки](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [Скачайте [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] для установки на компьютерах с Windows](https://go.microsoft.com/fwlink/?LinkID=862101).
- Установите на компьютерах с Linux для [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) и [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Запустите на [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] в Docker](../linux/quickstart-install-connect-docker.md).