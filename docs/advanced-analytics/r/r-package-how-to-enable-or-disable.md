---
title: Включение или отключение управления удаленными пакетами R
description: Включение удаленного управления пакетами R в службах SQL Server 2016 R или SQL Server 2017 Службы машинного обучения (в базе данных)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 9cc08b1227751559ea509838fe8fc3a446296770
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470023"
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Включение или отключение управления удаленными пакетами для SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается, как включить удаленное управление пакетами R с клиентской рабочей станции или с другого Machine Learning Server. После включения функции управления пакетами на SQL Server можно использовать команды RevoScaleR на клиенте для установки пакетов на SQL Server.

> [!NOTE]
> Сейчас поддерживается управление библиотеками R; Поддержка Python включена в схему.

По умолчанию функция управления внешними пакетами для SQL Server отключена. Необходимо запустить отдельный скрипт, чтобы включить эту функцию, как описано в следующем разделе.

## <a name="overview-of-process-and-tools"></a>Общие сведения о процессах и средствах

Чтобы включить или отключить управление пакетами в SQL Server, используйте служебную программу командной строки **RegisterRExt. exe**, которая входит в состав пакета **RevoScaleR** .

[Включение](#bkmk_enable) этой функции — это двухэтапный процесс, в котором требуется администратор базы данных: вы включаете Управление пакетами на экземпляре SQL Server (один раз для каждого экземпляра SQL Server), а затем включаете Управление пакетами в базе данных SQL (один раз для каждой базы данных SQL Server ).

[Отключение](#bkmk_disable) функции управления пакетами также требует мултипел действий: вы удаляете пакеты и разрешения уровня базы данных (один раз для каждой базы данных), а затем удаляете роли с сервера (один раз для каждого экземпляра).

## <a name="bkmk_enable"></a>Включить управление пакетами

1. На SQL Server откройте командную строку с повышенными привилегиями и перейдите в папку с программой RegisterRExt. exe. Расположение по умолчанию `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`—.

2. Выполните следующую команду, указав соответствующие аргументы для вашей среды:

    `RegisterRExt.exe /install pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда создает объекты уровня экземпляра на SQL Server компьютере, которые необходимы для управления пакетами. Он также перезапустит панель запуска для экземпляра.

    Если экземпляр не указан, используется экземпляр по умолчанию. Если пользователь не указан, используется текущий контекст безопасности. Например, следующая команда включает управление пакетами для экземпляра в пути к RegisterRExt. exe, используя учетные данные пользователя, открывшего командную строку:

    `REgisterRExt.exe /install pkgmgmt`

3. Чтобы добавить Управление пакетами в определенную базу данных, выполните следующую команду в командной строке с повышенными привилегиями:

    `RegisterRExt.exe /install pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Эта команда создает некоторые артефакты базы данных, включая следующие роли базы данных, используемые для управления разрешениями `rpkgs-private`пользователей: `rpkgs-shared` `rpkgs-users`, и.

    Например, следующая команда включает управление пакетами в базе данных на экземпляре, где выполняется RegisterRExt. Если пользователь не указан, используется текущий контекст безопасности.

    `RegisterRExt.exe /install pkgmgmt /database:TestDB`

4. Повторите команду для каждой базы данных, в которой должны быть установлены пакеты.

5. Чтобы убедиться, что новые роли были успешно созданы, в SQL Server Management Studio щелкните базу данных, разверните узел **Безопасность**и разверните узел **роли базы данных**.

    Можно также выполнить запрос к sys. database_principals, как показано ниже:

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

После включения этой функции можно использовать функцию RevoScaleR для установки и удаления пакетов из удаленного клиента R.

## <a name="bkmk_disable"></a>Отключение управления пакетами

1. В командной строке с повышенными привилегиями снова запустите программу RegisterRExt и отключите Управление пакетами на уровне базы данных:

    `RegisterRExt.exe /uninstall pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет объекты базы данных, связанные с управлением пакетами, из указанной базы данных. Он также удаляет все пакеты, установленные из защищенного расположения файловой системы на SQL Server компьютере.

2. Повторите эту команду для каждой базы данных, в которой использовалось управление пакетами.

3.  Используемых После того как все базы данных будут удалены из пакетов с помощью предыдущего шага, выполните следующую команду в командной строке с повышенными привилегиями:

    `RegisterRExt.exe /uninstall pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Эта команда удаляет компонент управления пакетами из экземпляра. Чтобы увидеть изменения, может потребоваться вручную перезапустить службу панели запуска.

## <a name="next-steps"></a>Следующие шаги

+ [Установка новых пакетов R с помощью RevoScaleR](use-revoscaler-to-manage-r-packages.md)
+ [Советы по установке пакетов R](packages-installed-in-user-libraries.md)
+ [Пакеты по умолчанию](../package-management/default-packages.md)
