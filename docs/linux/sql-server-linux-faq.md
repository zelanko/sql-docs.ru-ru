---
title: "SQL Server в Linux часто задаваемые вопросы | Документы Microsoft"
description: "В этой статье содержатся ответы на часто задаваемые вопросы о SQL Server под управлением Linux."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Active
ms.openlocfilehash: 3fad3fb2892e5a91e42eefb5f00932c39d00064f
ms.sourcegitcommit: f0c5e37c138be5fb2cbb93e9f2ded307665b54ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/24/2018
---
# <a name="sql-server-on-linux-frequently-asked-questions-faq"></a>SQL Server в Linux, часто задаваемые вопросы (FAQ)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В следующих разделах общих вопросов и ответов для SQL Server под управлением Linux.

## <a name="general-questions"></a>Общие вопросы

1. **Какие платформы Linux поддерживаются?**

   В настоящее время поддерживается SQL Server в Red Hat Enterprise Server, SUSE Linux Enterprise Server и Ubuntu. Он также выполняется в контейнер с помощью Docker. Последние сведения о поддерживаемых версиях см. в разделе [поддерживаемых платформ](sql-server-linux-setup.md#supportedplatforms).

1. **SQL Server в Linux будут работать на других платформах**?

   Возможно, можно установить и запустить SQL Server на других дистрибутивов Linux. Например CentOS тесно связана с Red Hat Enterprise Server, поэтому возможно установить пакеты RPM SQL Server. Это может быть верно для других распределений тесно связанных между собой. Основная проблема заключается в тестировании и поддержки. SQL Server протестирован только и поддерживается только в Red Hat Enterprise Linux, SUSE Linux Enterprise Server и Ubuntu.

1. **Поддерживаемых возможностях SQL Server в Linux?**

   Полный список поддерживаемых функций и известных проблемах см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

1. **Что такое политика поддержки для SQL Server**

   Чтобы понять политику поддержки, просмотрите [технической поддержки политики для SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

1. **Небезопасного фона Windows SQL Server Существуют ресурсы, которые помогут освоить использование SQL Server в Linux?**

   [Краткие руководства](sql-server-linux-setup.md#platforms) приведены пошаговые инструкции по установке SQL Server в Linux и запускать запросы Transact-SQL. Других учебниках содержатся дополнительные инструкции по использованию SQL Server в Linux. Список сторонних советы см. в разделе [MSSQLTIPS список SQL Server в Linux советы](https://www.mssqltips.com/sql-server-tip-category/226/sql-server-on-linux/).

## <a name="installation"></a>Установка

1. **Как получить SQL Server, установленных на серверах my Linux?**

   Корпорация Майкрософт поддерживает репозитории пакета для установки SQL Server и поддерживает установку с помощью диспетчерами пакета машинного кода, например yum zypper кв. Чтобы быстро установить, см. в одном из [краткие руководства](sql-server-linux-setup.md#platforms).

1. **Можно установить SQL Server в Linux подсистемы для Windows 10**

   Нет. ОС Linux работает в Windows 10 в настоящее время не является поддерживаемой платформой для SQL Server, а также связанные средства.

1. **Какие файловые системы Linux 2017 г. SQL Server можно использовать для файлов данных?**

   В настоящее время SQL Server в Linux поддерживает ext4 и XFS. При необходимости в будущем будет добавить поддержку для других файловых систем.

1. **Можно загрузить установочные пакеты для автономной установки SQL Server**

   Да. Дополнительные сведения см. в разделе пакет загрузки ссылки в [заметки о выпуске](sql-server-linux-release-notes.md). Кроме того, просмотрите [инструкции для автономной установки](sql-server-linux-setup.md#offline).

1. **Можно выполнять автоматической установки SQL Server в Linux**

   Да. Сведения об автоматической установке см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md#unattended). См. Примеры сценариев для [Red Hat](sample-unattended-install-redhat.md), [SUSE Linux Enterprise Server](sample-unattended-install-suse.md), и [Ubuntu](sample-unattended-install-ubuntu.md). Можно также просмотреть [сценарий](https://blogs.msdn.microsoft.com/sqlcat/2017/10/03/unattended-install-and-configuration-for-sql-server-2017-on-linux/) созданные группа консультантов по SQL Server клиента.

## <a name="tools"></a>Средства

1. **Можно ли использовать клиент SQL Server Management Studio в Windows для доступа к SQL Server в Linux?**

   Да, можно использовать свои имеющиеся средства, которые работают в Windows для доступа к SQL Server в Linux. Сюда входят средства от Майкрософт, таких как SQL Server Management Studio (SSMS), SQL Server Data Tools (SSDT) и операционные системы и сторонних разработчиков.

1. **Есть средства, подобного SSMS, которая выполняется на платформе Linux?**

   Новые операции Studio Microsoft SQL (Предварительная версия) — это средство кросс платформенных управления SQL Server. Дополнительные сведения см. в разделе [возможности Microsoft SQL Studio (Предварительная версия) для операций](../sql-operations-studio/what-is.md).

1. **Команды sqlcmd и bcp доступны в Linux?**

   Да, [sqlcmd и bcp](sql-server-linux-setup-tools.md) изначально доступны на macOS, Windows и Linux. Кроме того, использовать новую [mssql-scripter](https://github.com/Microsoft/mssql-scripter) средство командной строки в Linux, macOS или Windows, для создания скриптов T-SQL для выполнения в любом месте базы данных SQL. Кроме того, в разделе о выпуске предварительной версии [mssql cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/).

1. **Возможно, для просмотра монитора активности при подключении через SSMS в Windows для экземпляра выполняется на платформе Linux?**

   Да, среда SSMS в Windows можно использовать для удаленного подключения и использования Сервис / таких функций, как команды монитора активности в экземпляре Linux.

1. **Какие средства доступны для наблюдения за производительностью SQL Server в Linux?**

   Можно использовать [системных динамических административных представлений (DMV)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) собирать различные типы сведений о SQL Server, включая сведения о процессе Linux. Можно использовать [хранилище запросов](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md) для повышения производительности запросов. Другие средства, такие как встроенные [панели мониторинга производительности](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)работает удаленно в SQL Server Management Studio (SSMS) из Windows.

## <a name="administration"></a>Администрирование

1. **Корпорация Майкрософт создала приложение как диспетчер конфигурации SQL Server в Linux**

   Да, имеется configuration tool для SQL Server в Linux: [mssql conf](sql-server-linux-configure-mssql-conf.md).

1. **SQL Server в Linux поддерживает несколько экземпляров на одном узле?**

   Рекомендуется запускать несколько контейнеров на узле, чтобы иметь несколько различных экземпляров. Каждый контейнер необходимо прослушивать другой порт. Дополнительные сведения см. в разделе [работает несколько контейнеров SQL Server](sql-server-linux-configure-docker.md#run-multiple-sql-server-containers).

1. **Поддерживается проверка подлинности Active Directory в Linux?**

   Да. Дополнительные сведения см. в разделе [проверки подлинности Active Directory с SQL Server в Linux](sql-server-linux-active-directory-authentication.md).

1. **Всегда активны и кластеризация поддерживается в Linux?**

   Отказоустойчивая кластеризация и высокий уровень доступности в Linux достигаются с Pacemaker в Linux. Дополнительные сведения см. в разделе [бизнеса бесперебойной работы и базы данных восстановления — SQL Server в Linux](sql-server-linux-business-continuity-dr.md).

1. **Можно настроить репликацию с Linux в Windows и наоборот?**

   Масштаб чтения реплики можно использовать между Windows и Linux для репликации данных.

1. **Это можно выполнить миграцию существующих баз данных в SQL Server более ранних версиях Windows для Linux?**

   Да, есть [несколько методов](sql-server-linux-migrate-overview.md) сделать это.

1. **Можно перенести данные из Oracle и других экземпляров компонента database Engine в SQL Server в Linux?**

   Да. SSMA поддерживается миграция из нескольких типов экземпляров компонента database Engine: Microsoft Access, DB2, MySQL, Oracle и SAP ASE (прежнее название — SAP Sybase ASE). Пример использования SSMA см. в разделе [переноса схемы Oracle для 2017 г. SQL Server в Linux с SQL Server Migration Assistant](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json).

1. **Разрешениях, необходимых для файлов SQL Server?**

   Все файлы в `/var/opt/mssql` папку файл должен принадлежать **mssql** пользователя и относящиеся к **mssql** группы. Оба **mssql** пользователей и групп должны иметь разрешения на чтение запись всех файлов и каталогов. Следует отметить следующие специальные сценарии, включающие разрешений файлов и каталогов.

   * Для подключенных сетевых дисков, используются для хранения файлов SQL Server требуются разрешения владельца mssql.
   * Если обнаружить файлы базы данных или резервные копии в каталоге не по умолчанию, необходимо также задать разрешения для этого каталога.
   * При переключении umask корневой по умолчанию из 0022 конфигурации SQL Server не работает после установки. Необходимо вручную применить необходимые разрешения для учетной записи для запуска SQL Server.

1. **Можно изменить владельца файлов SQL Server и каталогов из установленных mssql учетной записи и группы**

   Смена владельца каталога SQL Server и файлов из установки по умолчанию не поддерживают. Mssql учетной записи и группы используется специально для SQL Server и нет доступа на интерактивный вход в систему.

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]