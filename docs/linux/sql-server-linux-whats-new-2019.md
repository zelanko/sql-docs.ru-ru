---
title: Новые возможности SQL Server 2019 на Linux
description: В этой статье описываются новые возможности SQL Server 2019 на Linux.
author: VanMSFT
ms.author: vanto
ms.date: 10/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 5183efa51afd89ad82d0cdcb6448996429b81d28
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "72890558"
---
# <a name="whats-new-for-sql-server-2019-on-linux"></a>Новые возможности SQL Server 2019 на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описываются основные функции и службы, доступные для SQL Server 2019 на Linux. Дополнительные сведения и известные проблемы см. в статье с [заметками о выпуске](sql-server-linux-release-notes-2019.md?view=sql-server-linux-ver15).

## <a name="updates"></a>Обновления

Обновления в SQL Server 2019 на Linux:

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Поддержка репликации. |[Репликация SQL Server в Linux](sql-server-linux-replication.md)
|Поддержка координатора распределенных транзакций Майкрософт (MSDTC). |[Настройка MSDTC на платформе Linux](sql-server-linux-configure-msdtc.md) |
|Поддержка OpenLDAP для сторонних поставщиков Active Directory. |[Руководство. Использование проверки подлинности Azure Active Directory с SQL Server на Linux](sql-server-linux-active-directory-authentication.md) |
|Поддержка машинного обучения в Linux. |[Настройка машинного обучения в Linux](sql-server-linux-setup-machine-learning.md) |
|Улучшения `tempdb` | По умолчанию новая установка SQL Server на Linux создает несколько файлов данных `tempdb` на основе числа логических ядер (до 8 файлов данных). Это не применимо к обновлениям основной или дополнительной версии на месте. Размер каждого файла `tempdb` составляет 8 МБ с возможностью автоматического увеличения до 64 МБ. Это поведение аналогично поведению установки SQL Server по умолчанию в Windows. |
| PolyBase на компьютерах под управлением Linux | [Установка PolyBase](../relational-databases/polybase/polybase-linux-setup.md) в Linux для соединителей вне Hadoop.<br/><br/>[Сопоставление типов PolyBase](../relational-databases/polybase/polybase-type-mapping.md). |
| Поддержка системы отслеживания измененных данных (CDC) | Система отслеживания измененных данных (CDC) теперь поддерживается в Linux для SQL Server 2019. |
| Реестр контейнеров Майкрософт | [Реестр контейнеров Майкрософт](https://www.ntweekly.com/2019/09/23/microsoft-container-registry-to-replace-docker-hub-for-new-images/) теперь заменяет Docker Hub в качестве источника новых официальных образов контейнеров Майкрософт, включая [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |
| Непривилегированные контейнеры | [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет возможность создания более безопасных контейнеров путем запуска процесса [!INCLUDE[sql-server](../includes/ssnoversion-md.md)] по умолчанию от имени пользователя, не являющегося привилегированным. См. раздел [Сборка и запуск контейнеров SQL Server от имени непривилегированного пользователя](sql-server-linux-configure-docker.md#buildnonrootcontainer). |

## <a name="next-steps"></a>Дальнейшие действия

Чтобы установить SQL Server на Linux, используйте один из следующих учебников:

- [Установка в Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md?view=sql-server-linux-ver15)
- [Установка в SUSE Linux Enterprise Server](quickstart-install-connect-suse.md?view=sql-server-linux-ver15)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md?view=sql-server-linux-ver15)
- [Запуск в Docker](quickstart-install-connect-docker.md?view=sql-server-linux-ver15)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

Ответы на часто задаваемые вопросы об SQL Server на Linux см. в [этой статье](sql-server-linux-faq.md). Дополнительные сведения об улучшениях, появившихся в SQL Server 2019, см. в разделе [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
