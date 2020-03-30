---
title: Включение и отключение удаленного управления пакетами R
description: Включение удаленного управления пакетами R в службах SQL Server 2016 R Services или Службах машинного обучения SQL Server (в базе данных)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: =sql-server-2016||=sql-server-2017||=sqlallproducts-allversions
ms.openlocfilehash: 250be5c8a4207a43d2e4194c78377bd87880a99c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74485239"
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Включение и отключение удаленного управления пакетами для SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается, как включить удаленное управление пакетами R с клиентской рабочей станции или с другого Machine Learning Server. После включения функции управления пакетами в экземпляре SQL Server можно использовать команды RevoScaleR на клиенте для установки пакетов в этом экземпляре.

По умолчанию функция управления внешними пакетами для SQL Server отключена. Чтобы включить эту функцию, необходимо запустить отдельный скрипт, как описано в следующем разделе.

## <a name="overview-of-process-and-tools"></a>Общие сведения о процессе и инструментах

Для включения или отключения управления пакетами для SQL Server используйте программу командной строки **RegisterRExt.exe**, входящую в состав пакета **RevoScaleR**.

[Включение](#bkmk_enable) этой функции состоит из двух этапов. При этом требуется роль администратора базы данных. Вы включаете управление пакетами в экземпляре SQL Server (один раз для каждого экземпляра SQL Server), а затем в базе данных SQL (один раз для каждой базы данных SQL Server).

[Отключение](#bkmk_disable) функции управления пакетами также требует нескольких действий. Вы сначала удаляете пакеты и разрешения на уровне базы данных (один раз для каждой базы данных), а затем — роли с сервера (один раз для каждого экземпляра).

## <a name="enable-package-management"></a><a name="bkmk_enable"></a> Включение управления пакетами

1. На SQL Server откройте командную строку с повышенными привилегиями и перейдите в папку, содержащую программу RegisterRExt.exe. Расположение по умолчанию — `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Выполните следующую команду, указав соответствующие аргументы для вашей среды:

    `RegisterRExt.exe /install pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда создает на компьютере SQL Server объекты уровня экземпляра, которые требуются для управления пакетами. Также выполнится перезапуск панели запуска для экземпляра.

    Если экземпляр не указан, используется экземпляр по умолчанию. Если пользователь не указан, используется текущий контекст безопасности. Например, следующая команда включает управление пакетами для экземпляра в пути к RegisterRExt.exe, используя учетные данные пользователя, открывшего командную строку:

    `REgisterRExt.exe /install pkgmgmt`

3. Из командной строки с повышенными привилегиями выполните следующую команду, чтобы добавить управление пакетами к указанной базе данных:

    `RegisterRExt.exe /install pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Эта команда создает некоторые артефакты базы данных, включая следующие роли базы данных, которые используются для управления разрешениями пользователей: `rpkgs-users`, `rpkgs-private` и `rpkgs-shared`.

    Например, следующая команда включает управление пакетами в базе данных экземпляра, где выполняется RegisterRExt. Если пользователь не указан, используется текущий контекст безопасности.

    `RegisterRExt.exe /install pkgmgmt /database:TestDB`

4. Повторите эту команду для каждой базы данных, в которой должны быть установлены пакеты.

5. Чтобы убедиться, что новые роли успешно созданы, в SQL Server Management Studio щелкните базу данных, разверните узел **Безопасность**, а затем **Роли базы данных**.

    Можно также выполнить запрос к sys.database_principals, как показано ниже:

    ```sql
    SELECT pr.principal_id, pr.name, pr.type_desc,   
        pr.authentication_type_desc, pe.state_desc,   
        pe.permission_name, s.name + '.' + o.name AS ObjectName  
    FROM sys.database_principals AS pr  
    JOIN sys.database_permissions AS pe  
        ON pe.grantee_principal_id = pr.principal_id  
    JOIN sys.objects AS o  
        ON pe.major_id = o.object_id  
    JOIN sys.schemas AS s  
        ON o.schema_id = s.schema_id;
    ```

После включения этой возможности можно использовать функцию RevoScaleR для установки и удаления пакетов из удаленного клиента R.

## <a name="disable-package-management"></a><a name="bkmk_disable"></a> Отключение управления пакетами

1. Из командной строки с повышенными привилегиями снова запустите программу RegisterRExt и отключите управление пакетами на уровне базы данных:

    `RegisterRExt.exe /uninstall pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет объекты базы данных, связанные с управлением пакетами, из указанной базы данных. Кроме того, она удаляет все пакеты, которые были установлены из защищенного расположения файловой системы на компьютере с SQL Server.

2. Повторите эту команду для каждой базы данных, в которой использовалось управление пакетами.

3.  (Необязательно.) После очистки всех баз данных от пакетов с помощью предыдущего действия выполните следующую команду из командной строки с повышенными привилегиями:

    `RegisterRExt.exe /uninstall pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет из экземпляра функцию управления пакетами. Чтобы увидеть изменения, может потребоваться вручную перезапустить службу панели запуска.

## <a name="next-steps"></a>Дальнейшие действия

+ [Установка пакетов R с помощью RevoScaleR](install-r-packages-with-revoscaler.md)
+ [Получение сведений о пакете R](r-package-information.md)
+ [Советы по использованию пакетов R](tips-for-using-r-packages.md)
