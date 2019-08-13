---
title: Новые возможности SQL Server 2017 на Linux
description: В этой статье описываются новые возможности SQL Server 2017 на Linux.
author: VanMSFT
ms.author: vanto
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.openlocfilehash: 3f3f51716acf69368ae2554446c47d125b500e03
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032160"
---
# <a name="whats-new-for-sql-server-on-linux"></a>Новые возможности SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описываются основные функции и службы, доступные для SQL Server 2017 на Linux.

Выпущена предварительная версия SQL Server 2019. Эта статья не охватывает предварительные выпуски SQL Server 2019. Дополнительные сведения о предварительной версии SQL Server 2019 см. в статье [Новые возможности в предварительной версии SQL Server 2019 на Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

> [!NOTE]
> Помимо описанных ниже возможностей, следует отметить накопительные обновления, которые регулярно выпускаются после выхода общедоступной версии. Эти накопительные обновления содержат много усовершенствований и исправлений. Просмотреть сведения о последнем выпуске накопительного обновления можно здесь: [https://aka.ms/sql2017cu](https://aka.ms/sql2017cu). Дополнительные сведения и известные проблемы см. в статье с [заметками о выпуске](sql-server-linux-release-notes.md).

## <a name="sql-server-database-engine"></a>Компонент SQL Server Database Engine

- Включены основные возможности ядра СУБД SQL Server.
- Поддержка собственных путей Linux.
- Поддержка IPV6.
- Поддержка файлов баз данных на NFS.
- Поддержка шифрования [Transport Layer Security](sql-server-linux-encrypted-connections.md) (TLS).
- Поддерживается [проверка подлинности Azure Active Directory](sql-server-linux-active-directory-authentication.md).
- [Функции групп доступности](sql-server-linux-availability-group-overview.md) для обеспечения высокой доступности.
- [Поддержка полнотекстового поиска](sql-server-linux-setup-full-text-search.md).

## <a name="sql-server-agent"></a>Агент SQL Server

- Включена поддержка [агента SQL Server](sql-server-linux-setup-sql-agent.md) для следующих задач:
  - [Задания Transact-SQL](sql-server-linux-run-sql-server-agent-job.md)
  - [Почта базы данных](sql-server-linux-db-mail-sql-agent.md)
  - [доставка журналов;](sql-server-linux-use-log-shipping.md)

## <a name="sql-server-integration-services-ssis"></a>Службы SQL Server Integration Services (SSIS)

- Возможность выполнять пакеты SSIS на Linux. Дополнительные сведения см. в разделе [Настройка SQL Server Integration Services в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="other-improvements"></a>Другие усовершенствования

- Средство настройки командной строки [mssql-conf](sql-server-linux-configure-mssql-conf.md).
- [Переменные среды](sql-server-linux-configure-environment-variables.md) для автоматической установки.
- Кроссплатформенное [расширение Visual Studio Code mssql-server](sql-server-linux-develop-use-vscode.md).
- Кроссплатформенный генератор сценариев, [mssql-scripter](https://github.com/Microsoft/sql-xplat-cli/blob/dev/doc/usage_guide.md).
- Кроссплатформенный монитор динамического административного представления (DMV), [средство DBFS](https://github.com/Microsoft/dbfs).

## <a name="next-steps"></a>Следующие шаги

Чтобы установить SQL Server на Linux, используйте один из следующих учебников:

- [Установка в Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка в SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запуск в Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

Дополнительные сведения об улучшениях, появившихся в SQL Server 2017, см. в разделе [Новые возможности SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

> [!TIP]
> Ответы на часто задаваемые вопросы об SQL Server на Linux см. в [этой статье](sql-server-linux-faq.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
