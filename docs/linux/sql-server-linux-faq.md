---
title: SQL Server в Linux часто задаваемые вопросы | Документация Майкрософт
description: В этой статье содержатся ответы на часто задаваемые вопросы о SQL Server на платформе Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 448db7c77d26e06651e01a7e790917757aff0e9d
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713606"
---
# <a name="sql-server-on-linux-frequently-asked-questions-faq"></a>SQL Server в Linux, часто задаваемые вопросы (FAQ)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Следующие разделы содержат общие вопросы и ответы для SQL Server на платформе Linux.

## <a name="general-questions"></a>Общие вопросы

1. **Поддерживаемых платформах Linux?**

   В настоящее время поддерживается SQL Server в Red Hat Enterprise Server, SUSE Linux Enterprise Server и Ubuntu. Также поддерживается, работающий в контейнере с помощью Docker. Последние сведения о поддерживаемых версиях см. в разделе [поддерживаемые платформы](sql-server-linux-setup.md#supportedplatforms).

1. **SQL Server в Linux будут работать на других платформах**?

   SQL Server протестированы и поддерживаются в Linux, перечисленные выше дистрибутивов. Другие дистрибутивы Linux, тесно связаны и может иметь возможность запускать SQL Server (например, CentOS тесно связано с Red Hat Enterprise Server). Но если вы решили установить SQL Server в неподдерживаемой операционной системе, просмотрите **политика поддержки** раздел [политики технической поддержки для Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server) о поддержке последствия. Обратите внимание на то, что некоторые-Поддерживаемые сообществом дистрибутивов Linux, нет формальных способ получить поддержку, если базовая операционная система — это проблема.

1. **Как работает лицензирование в Linux?**

   Так же, как лицензия SQL Server для Windows и Linux. На самом деле лицензии SQL Server, а затем вы можете использовать эту лицензию на платформе по своему усмотрению. Дополнительные сведения см. в разделе [как лицензии SQL Server](https://www.microsoft.com/sql-server/sql-server-2017-pricing).

1. **Является SQL Server в Linux так же, как и в Windows?**

   Ядро СУБД для SQL Server является одинаковым на Linux как при использовании Windows. Тем не менее некоторые функции в настоящее время не поддерживаются в Linux. Список компонентов, которые не поддерживаются в Linux, см. в разделе [неподдерживаемые функции и службы](sql-server-linux-release-notes.md#Unsupported). Кроме того, просмотрите [известные проблемы](sql-server-linux-release-notes.md#known-issues). Если не указано в этих списках, на платформе Linux поддерживаются другие функции SQL Server и службы.

1. **Какова политика поддержки для SQL Server?**

   Сведения о политике поддержки, см. в статье [технические политики поддержки для SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

1. **Я поступающих из фона Windows SQL Server. Существуют ресурсы, которые помогут научиться использовать SQL Server в Linux?**

   [Краткие руководства](sql-server-linux-setup.md#platforms) содержат пошаговые инструкции о том, как установить SQL Server на Linux и запускать запросы Transact-SQL. Других руководствах содержатся дополнительные инструкции по использованию SQL Server в Linux. Для независимых производителей список советов, см. в разделе [MSSQLTIPS список SQL Server на Linux советы](https://www.mssqltips.com/sql-server-tip-category/226/sql-server-on-linux/).

## <a name="installation"></a>Установка

1. **Как получить SQL Server, установленный на Мои серверы Linux?**

   Корпорация Майкрософт поддерживает репозитории пакета для установки SQL Server и поддерживает установку с помощью диспетчерами пакета машинного кода, например yum, zypper дом. Чтобы быстро установить, см. в одном из [краткие руководства](sql-server-linux-setup.md#platforms).

1. **Можно ли установить SQL Server на Linux подсистемы для Windows 10?**

   Нет. Linux под управлением Windows 10 в настоящее время не является поддерживаемой платформой для SQL Server, а также связанные средства.

1. **Какие файловые системы Linux SQL Server можно использовать для файлов данных?**

   В настоящее время SQL Server в Linux поддерживает ext4 и XFS. Будет добавлена поддержка другие файловые системы, при необходимости в будущем.

1. **Можно загрузить установочные пакеты для установки SQL Server в автономном режиме?**

   Да. Дополнительные сведения см. в разделе загрузки ссылки в пакет [заметки о выпуске](sql-server-linux-release-notes.md). Кроме того, просмотрите [инструкции для автономной установки](sql-server-linux-setup.md#offline).

1. **Можно выполнять автоматической установки SQL Server в Linux?**

   Да. Сведения по автоматической установке, см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md#unattended). См. в разделе Примеры сценариев для [Red Hat](sample-unattended-install-redhat.md), [SUSE Linux Enterprise Server](sample-unattended-install-suse.md), и [Ubuntu](sample-unattended-install-ubuntu.md). Вы также можете просмотреть [этот пример сценария](https://blogs.msdn.microsoft.com/sqlcat/2017/10/03/unattended-install-and-configuration-for-sql-server-2017-on-linux/) созданные группы консультирования клиентов SQL Server.

## <a name="tools"></a>Инструменты

1. **Можно ли использовать клиент SQL Server Management Studio на Windows для доступа к SQL Server в Linux?**

   Да, можно использовать все имеющиеся у вас инструменты, работающие на Windows для доступа к SQL Server в Linux. К ним относятся инструменты от корпорации Майкрософт, таких как SQL Server Management Studio (SSMS), SQL Server Data Tools (SSDT) и OSS и сторонние средства.

1. **Есть ли это средство, как среда SSMS, под управлением Linux?**

   Новый Studio данных Azure (Предварительная версия) — это кросс платформенного средства управления SQL Server. Дополнительные сведения см. в разделе [что такое студия данных Azure (Предварительная версия)](../azure-data-studio/what-is.md).

1. **Команды sqlcmd и bcp доступны на платформе Linux?**

   Да, [sqlcmd и bcp](sql-server-linux-setup-tools.md) встроена в Linux, macOS и Windows. Кроме того, использовать новую [mssql scripter](https://github.com/Microsoft/mssql-scripter) средство командной строки Linux, macOS или Windows для создания скриптов T-SQL для базы данных SQL под управлением любого места. Кроме того, см. в разделе о выпуске предварительной версии [mssql-cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/).

1. **Возможно, для просмотра монитора активности при подключении через SSMS в Windows для экземпляра выполняется на платформе Linux?**

   Да, можно использовать SSMS в Windows для удаленного подключения и использования Сервис & gt; функции, такие как команды монитор активности в экземпляре Linux.

1. **Какие средства доступны для мониторинга производительности SQL Server в Linux?**

   Можно использовать [системные динамические административные представления (DMV)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) собирать различные виды информации о SQL Server, включая сведения о процессе Linux. Можно использовать [Query Store](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md) для повышения производительности запросов. Другие инструменты, такие как встроенная [панели мониторинга производительности](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)работает удаленно в SQL Server Management Studio (SSMS) из Windows.

   > [!TIP]
   > Чтобы правильно настроить операционную систему Linux и insance SQL Server является одним из способов повышения производительности. Дополнительные сведения см. в разделе [рекомендации по производительности и рекомендации по конфигурации для SQL Server в Linux](sql-server-linux-performance-best-practices.md).

## <a name="administration"></a>Администрирование

1. **Корпорация Майкрософт создала приложение как диспетчер конфигурации SQL Server в Linux**

   Да, есть средство настройки для SQL Server в Linux: [mssql-conf](sql-server-linux-configure-mssql-conf.md).

1. **Поддерживает ли SQL Server в Linux нескольких экземпляров на одном узле?**

   Мы рекомендуем выполнять несколько контейнеров на узле несколько отдельных экземпляров. Каждый контейнер необходимо прослушивать другой порт. Дополнительные сведения см. в разделе [запуск нескольких контейнеров SQL Server](sql-server-linux-configure-docker.md#run-multiple-sql-server-containers).

1. **Проверка подлинности Active Directory поддерживается на платформе Linux?**

   Да. Дополнительные сведения см. в разделе [проверки подлинности Active Directory с SQL Server в Linux](sql-server-linux-active-directory-authentication.md).

1. **Всегда включены и кластеризация поддерживается в Linux?**

   Отказоустойчивая кластеризация и высокая доступность в Linux обеспечивается с помощью Pacemaker в Linux. Дополнительные сведения см. в разделе [бизнес- непрерывности восстановление — SQL Server в Linux](sql-server-linux-business-continuity-dr.md).

1. **Это можно настроить репликацию с Linux на Windows и наоборот?**

   Для репликации данных между Windows и Linux можно использовать реплики для чтения и масштабирования.

1. **Это можно выполнить миграцию существующих баз данных в более ранних версиях SQL Server Windows для Linux?**

   Да, есть [несколько методов](sql-server-linux-migrate-overview.md) сделать это.

1. **Можно ли перенести данные из Oracle и других ядер СУБД SQL Server в Linux?**

   Да. SSMA поддерживается миграция из нескольких типов компонентов database Engine: Microsoft Access, DB2, MySQL, Oracle и SAP ASE (прежнее название — SAP Sybase ASE). Пример использования SSMA, см. в разделе [перенос схемы Oracle для SQL Server в Linux с помощью SQL Server Migration Assistant](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json).

1. **Разрешениях, необходимых для файлов SQL Server?**

   Все файлы в `/var/opt/mssql` папку файл должен принадлежать **mssql** пользователя и принадлежат **mssql** группы. Оба **mssql** пользователей и групп должны иметь разрешения на чтение запись всех файлов и каталогов. Обратите внимание, следующих особых сценариев, включающих разрешений файлов и каталогов:

   * Для подключенных сетевых ресурсов, которые используются для хранения файлов SQL Server требуются разрешения владельца mssql.
   * Если файлы базы данных или резервных копий в каталоге не по умолчанию, необходимо также задать разрешения для этого каталога.
   * Если изменить корневой umask по умолчанию 0022, сбой при настройке SQL Server после установки. Затем необходимо вручную применить необходимые разрешения для стартовой учетной записи SQL Server.

1. **Можно ли изменить владение SQL Server файлы и каталоги из установленных mssql учетной записи и группы?**

   Мы не поддерживаем изменение владельца каталога SQL Server и файлов установки по умолчанию. Mssql учетной записи и группы используется специально для SQL Server и не имеет интерактивного входа в систему доступа.

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
