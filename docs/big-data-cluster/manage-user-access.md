---
title: Управление доступом к кластеру больших данных в режиме AD DS
description: Управление доступом к кластеру больших данных
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 08/04/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ef2df0bec343d73de90a43e411da92530c3c50c8
ms.sourcegitcommit: 6ab28d954f3a63168463321a8bc6ecced099b247
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87790277"
---
# <a name="manage-big-data-cluster-access-in-active-directory-mode"></a>Управление доступом к кластеру больших данных в режиме AD DS

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается, как добавить новые группы Active Directory с ролями *bdcUser* в дополнение к тем, которые были предоставлены во время развертывания с помощью параметра конфигурации *clusterUsers*.

>[!IMPORTANT]
>Не используйте эту процедуру для добавления новых групп Active Directory с ролью *bdcAdmin*. Компоненты Hadoop, такие как HDFS и Spark, допускают только одну группу Active Directory в качестве группы суперпользователя — эквивалент роли *bdcAdmin* в BDC. Чтобы предоставить группам AD DS дополнительные разрешения *bdcAdmin* для кластера больших данных после развертывания, следует добавить пользователей и группы в уже назначенные группы во время развертывания. Вы можете выполнить ту же процедуру, чтобы обновить членство в группе с ролью *bdcUsers*.

## <a name="two-overarching-roles-in-the-big-data-cluster"></a>Две ключевые роли в кластере больших данных

Группы AD DS предоставляются в разделе безопасности профиля развертывания как часть двух ключевых ролей для авторизации в кластере больших данных:

* `clusterAdmins`: этот параметр принимает одну группу AD DS. Члены этой группы имеют роль *bdcAdmin*, то есть получают разрешения администратора для всего кластера. Они имеют разрешения *sysadmin* в SQL Server, *superuser* в распределенной файловой системе Hadoop (HDFS) и Spark, а также права *администратора* в контроллере.

* `clusterUsers`: Эти группы Active Directory сопоставляются с ролью *bdcUsers* в BDC. Это обычные пользователи без прав администратора в кластере. У них есть разрешения на вход в главный экземпляр SQL Server, но по умолчанию они не имеют разрешений на доступ к объектам или данным. Это обычные пользователи для HDFS и Spark, без разрешений *суперпользователя*. При подключении к конечной точке контроллера эти пользователи могут запрашивать только конечные точки (с помощью команды *azdata bdc endpoints list*).

Чтобы предоставить группам AD DS дополнительные разрешения *bdcUser* без изменения членства в группах в AD DS, выполните процедуры, описанные в следующих разделах.

## <a name="grant-bdcuser-permissions-to-additional-active-directory-groups"></a>Предоставление разрешений *bdcUser* для дополнительных групп Active Directory

### <a name="create-a-login-for-the-active-directory-user-or-group-in-the-sql-server-master-instance"></a>Создание имени входа для пользователя AD DS или группы в главном экземпляре SQL Server

1. Подключитесь к главной конечной точке SQL с использованием избранного клиента SQL. Используйте любое имя входа администратора (например `AZDATA_USERNAME`, которое было предоставлено во время развертывания). Кроме того, это может быть любая учетная запись AD DS, которая входит в группу AD DS, предоставленную как `clusterAdmins` в конфигурации безопасности.

1. Чтобы создать имя входа для пользователя или группы AD DS, выполните следующую команду TSQL:

   ```sql
   CREATE LOGIN [<domain>\<principal>] FROM WINDOWS;
   ```

   Предоставьте необходимые разрешения в экземпляре SQL Server:

   ```sql
   ALTER SERVER ROLE <server role> ADD MEMBER [<domain>\<principal>];
   GO
   ```

Полный список ролей сервера см. в соответствующем разделе о безопасности SQL Server [здесь](../relational-databases/security/authentication-access/server-level-roles.md).

### <a name="add-the-active-directory-user-or-group-to-the-roles-table-in-the-controller-database"></a>Добавление пользователя или группы AD DS в таблицу ролей в базе данных контроллера

1. Получите учетные данные SQL Server контроллера, выполнив следующие команды:

   а. Выполните эту команду от имени администратора Kubernetes:

   ```bash
   kubectl get secret controller-sa-secret -n <cluster name> -o yaml | grep password
   ```

   b. Декодируйте секрет из кодировки Base64.

   ```bash
   echo <password from kubectl command>  | base64 --decode && echo
   ```

1. В отдельном командном окне предоставьте порт сервера базы данных контроллера:

   ```bash
   kubectl port-forward controldb-0 1433:1433 --address 0.0.0.0 -n <cluster name>
   ```

1. Используйте предыдущее подключение для вставки новой строки в таблицы *roles* и *active_directory_principals*. Введите значение *REALM* в формате верхнего регистра.

   ```sql
   USE controller;
   GO

   INSERT INTO [controller].[auth].[roles] VALUES (N'<user or group name>@<REALM>', 'bdcUser')
   GO

   INSERT INTO [controller].[auth].[active_directory_principals] VALUES (N'<user or group name>@<REALM>', N'<SID>')
   GO
   ```

   Чтобы найти ИД безопасности пользователя или добавляемой группы, можно использовать команды PowerShell [Get-ADUser](/powershell/module/addsadministration/get-aduser/) или [Get-ADGroup](/powershell/module/addsadministration/get-adgroup/).

2. Убедитесь, что добавленные члены группы имеют ожидаемые разрешения *bdcUser*, выполнив вход на конечную точку контроллера или пройдя проверку подлинности в основном экземпляре SQL Server. Пример:

   ```bash
   azdata login
   azdata bdc endpoints list
   ```

## <a name="next-steps"></a>Дальнейшие действия

- [Основные понятия безопасности для работы с кластерами больших данных SQL Server 2019](concept-security.md)
