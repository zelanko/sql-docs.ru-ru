---
title: Новые возможности SQL Server 2017 на платформе Linux | Документация Майкрософт
description: В данной статье рассматриваются новые возможности SQL Server 2017 в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.openlocfilehash: c2a2d7d479521d3925e1420b0caad77fccccf15c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631582"
---
# <a name="whats-new-for-sql-server-on-linux"></a>Новые возможности SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описываются основные функции и службы, доступные для SQL Server 2017 на платформе Linux.

Предварительная версия SQL Server 2019 была отпущена. В этой статье рассматриваются предварительные выпуски SQL Server 2019. Дополнительные сведения о предварительной версии SQL Server 2019, см. в разделе [новые возможности в предварительной версии SQL Server 2019 для Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sqllinux).

> [!NOTE]
> Помимо этих возможностей в этой статье накопительные обновления выпускаются с регулярными интервалами после выпуска общедоступной версии. Эти накопительные обновления содержат много усовершенствований и исправлений. Сведения о последнем выпуске Накопительного, см. в разделе [ http://aka.ms/sql2017cu ](http://aka.ms/sql2017cu). Загрузка пакетов и известные проблемы, см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

## <a name="sql-server-database-engine"></a>Компонент SQL Server Database Engine

- Включить основные возможности SQL Server Database Engine.
- Поддержка собственных путей Linux.
- Поддержка IPv6.
- Поддержку файлов баз данных в NFS.
- Включить [прозрачный слой безопасности](sql-server-linux-encrypted-connections.md) шифрования (TLS).
- Включить [проверки подлинности Active Directory](sql-server-linux-active-directory-authentication.md).
- [Функции групп доступности](sql-server-linux-availability-group-overview.md) для обеспечения высокой доступности.
- [Компонент Full-text Search](sql-server-linux-setup-full-text-search.md) поддержки.

## <a name="sql-server-agent"></a>Агент SQL Server

- Включить [агента SQL Server](sql-server-linux-setup-sql-agent.md) поддержки для выполнения следующих задач:
  - [Задания Transact-SQL](sql-server-linux-run-sql-server-agent-job.md)
  - [Компонента DB mail](sql-server-linux-db-mail-sql-agent.md)
  - [доставка журналов;](sql-server-linux-use-log-shipping.md)

## <a name="sql-server-integration-services-ssis"></a>Службы SQL Server Integration Services

- Возможность запускать пакеты служб SSIS в Linux. Дополнительные сведения см. в разделе [настроить SQL Server Integration Services в Linux с помощью служб ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="other-improvements"></a>Другие усовершенствования

- Средство командной строки настройки, [mssql-conf](sql-server-linux-configure-mssql-conf.md).
- Поддержка автоматической установки с [переменные среды](sql-server-linux-configure-environment-variables.md).
- Кросс платформенные [расширения mssql-server, Visual Studio Code](sql-server-linux-develop-use-vscode.md).
- Генератор скриптов кросс платформенных, [mssql-scripter](https://github.com/Microsoft/sql-xplat-cli/blob/dev/doc/usage_guide.md).
- Монитор кросс платформенных динамическое административное представление (DMV), [DBFS средство](https://github.com/Microsoft/dbfs).

## <a name="next-steps"></a>Следующие шаги

Для установки SQL Server в Linux, используйте один из следующих руководств:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустить в Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

Другие улучшения, появившиеся в SQL Server 2017, см. в разделе [новые возможности в SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

> [!TIP]
> Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](sql-server-linux-faq.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
