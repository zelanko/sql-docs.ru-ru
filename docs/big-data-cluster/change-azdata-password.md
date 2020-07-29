---
title: Обновление AZDATA_PASSWORD
description: Обновление `AZDATA_PASSWORD` вручную
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 12/19/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a3121351fce1ef6c86575789cee5dbb2860ce3c9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728808"
---
# <a name="manually-update-azdata_password"></a>Ручное обновление `AZDATA_PASSWORD`

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

`AZDATA_PASSWORD` задается во время развертывания, независимо от того, работает ли кластер с интеграцией Active Directory. Он обеспечивает базовую проверку подлинности для контроллера кластера и главного экземпляра. В этом документе описано, как вручную обновить `AZDATA_PASSWORD`.

## <a name="change-azdata_password-for-controller"></a>Изменение `AZDATA_PASSWORD` для контроллера

Если кластер работает в режиме без Active Directory, обновите пароль шлюза Apache Knox, выполнив следующие действия.

1. Получите учетные данные контроллера SQL Server, выполнив следующие команды:

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
 
1. Используйте только что полученный пароль системного администратора для подключения к серверу базы данных контроллера из клиентского средства SQL.

1. Создайте новый сложный пароль для `AZDATA_USERNAME`, чтобы заменить существующий `AZDATA_PASSWORD`.

   Для упрощения примера следующие шаги используют "newPassword", потому что созданный пароль — это "newPassword". 

1. Получите `hexsalt` из пользовательской таблицы:

   ```sql
   SELECT hexsalt FROM [auth].[users] WHERE username = '<username>'
   ```

   `hexsalt` возвращает случайную шестнадцатеричную строку (например, `64FC59DF31244FFEE02F457BC0750226`).

1. Зашифруйте новый сложный пароль с помощью `hexsalt`.

   Для вашего удобства мы предоставляем готовый инструмент `pbkdf2` для шифрования пароля. Скачайте подходящее для платформы приложение .NET Core для [`pbkdf2`](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/security/password-hashing/pbkdf2/prebuilt-binaries).

   Приложение является самодостаточным и не требует никаких предварительных условий, таких как среда выполнения .NET. Чтобы зашифровать пароль выполните команду:

   ```bash
   pbkdf2 <password> <hexsalt>
   J2y4E4dhlgwHOaRr3HKiiVAKBfjuGDyYmzn88VXmrzM=
   ```

1. Обновите пароль в пользовательской таблице:

   ```SQL
   UPDATE [auth].[users] SET password = 'J2y4E4dhlgwHOaRr3HKiiVAKBfjuGDyYmzn88VXmrzM=' WHERE username = '<username>'
   ```

## <a name="change-azdata_password-in-the-sql-server-master-instance"></a>Изменение `AZDATA_PASSWORD` в главном экземпляре SQL Server

1. Подключитесь к главной конечной точке SQL с помощью любого пользователя-администратора.

1. Чтобы изменить пароль для учетных данных, которые вы определили во время развертывания в параметре `AZDATA_USERNAME`, выполните следующую команду TSQL:

   ```sql
   ALTER LOGIN <AZDATA_USERNAME> WITH PASSWORD = 'newPassword'
   ```
