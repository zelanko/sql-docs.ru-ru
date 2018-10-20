---
title: Изучите ресурсы Azure SQL с помощью обозревателя ресурсов Azure | Документация Майкрософт
description: Узнайте, как для обзора и управления Azure SQL Server, базы данных SQL Azure и управляемый экземпляр SQL Azure через обозреватель ресурсов Azure.
author: yanancai
ms.author: yanacai
manager: craigg
ms.date: 09/24/2018
ms.topic: quickstart
ms.prod: sql
ms.technology: azure-data-studio
ms.openlocfilehash: 5b969ded699c11414c1822c0cb455ee84dfa212f
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356065"
---
# <a name="explore-azure-sql-resources-with-azure-resource-explorer"></a>Изучите ресурсы Azure SQL с помощью обозревателя ресурсов Azure

В этом документе вы узнаете, как могут просматривать и управлять Azure SQL Server, базы данных Azure SQL и ресурсы управляемый экземпляр SQL Azure с помощью обозревателя ресурсов Azure в [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)].

>[!NOTE]
>Обозреватель ресурсов Azure будут поддерживаться в предварительной версии SQL Server 2019 в октябре. После этого можно установить расширения предварительной версии через [Диспетчер расширений](extensions.md) или с помощью **файл** > **установить пакет из пакета VSIX**.


## <a name="connect-to-azure"></a>Подключение к Azure

После установки подключаемый модуль предварительной версии SQL Azure отобразится в строке меню слева. Щелкните значок, чтобы открыть обозреватель ресурсов Azure. Если вы не видите значок Azure, в строке меню слева щелкните правой кнопкой мыши и выберите **обозревателя ресурсов Azure**.

### <a name="add-an-azure-account"></a>Добавить учетную запись Azure

Чтобы просмотреть ресурсы SQL, связанные с учетной записью Azure, необходимо сначала добавить учетную запись для [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)].

1. Откройте **связанные учетные записи** диалогового окна через значок управления учетной записью, в левом нижнем или через **вход в Azure...**  ссылку в обозревателе ресурсов Azure.

    ![Войдите в Azure](media/azure-resource-explorer/sign-in-to-azure.png)

2. В **связанные учетные записи** диалоговое окно, нажмите кнопку **добавить учетную запись**.

    ![Добавить учетную запись Azure](media/azure-resource-explorer/add-an-azure-account.png)

3. Нажмите кнопку **копирование и открытие** чтобы открыть в браузере для проверки подлинности.

    ![Проверки подлинности откройте страницу в браузере](media/azure-resource-explorer/open-authentication-in-browser.png)

4. Вставить **пользовательский код** в веб-страницы и нажмите кнопку **Продолжить** для проверки подлинности.

    ![Проверка подлинности в браузере](media/azure-resource-explorer/authenticate-in-browser.png)

5. В [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)] должны теперь появиться вошедшего в учетной записи Azure в **связанные учетные записи** диалоговое окно.

    ![Учетная запись Azure в вошедшего в систему](media/azure-resource-explorer/signed-in-azure-account.png)

### <a name="add-more-azure-accounts"></a>Добавление учетных записей Azure

Несколько учетных записей Azure, поддерживаются в [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)]. Чтобы добавить учетные записи Azure, нажмите кнопку в правой верхней части **связанные учетные записи** диалогового окна и выполните те же действия с к добавлению раздела учетной записи Azure для добавления учетных записей Azure.

![Добавьте учетную запись Azure](media/azure-resource-explorer/add-more-azure-account.png)

### <a name="remove-an-azure-account"></a>Удаление учетной записи Azure

Чтобы удалить существующую регистрируются в учетной записи Azure:

1. Откройте **связанные учетные записи** диалогового окна через значок управления учетной записью в левом нижнем.
2. Нажмите кнопку **X** кнопку справа от учетной записи Azure, чтобы удалить его.

    ![Удалить учетную запись Azure](media/azure-resource-explorer/remove-azure-account.png)

## <a name="filter-subscription"></a>Фильтровать подписки

После входа в учетную запись Azure, все подписки, связанный с, которые отображают учетной записи Azure в обозревателе ресурсов Azure. Вы можете отфильтровать подписок для каждой учетной записи Azure.

1. Нажмите кнопку **подписки выберите** кнопку в правой части учетной записи Azure.

   ![Фильтровать подписки](media/azure-resource-explorer/filter-subscription.png)

2. Установите флажки для тех подписок учетной записи, вы хотите просмотреть, а затем нажмите кнопку **ОК**.

   ![Выберите подписку](media/azure-resource-explorer/select-subscription.png)

## <a name="explore-azure-sql-resources"></a>Изучите ресурсы Azure SQL

Чтобы перейти на ресурс Azure SQL в обозревателе ресурсов Azure, разверните учетные записи Azure и тип группы ресурсов.

Обозреватель ресурсов Azure в настоящее время поддерживает Azure SQL Server, базы данных SQL Azure и управляемый экземпляр SQL Azure.

## <a name="connect-to-azure-sql-resources"></a>Подключение к ресурсам Azure SQL

Обозреватель ресурсов Azure обеспечивают быстрый доступ, который позволяет подключаться к серверам SQL и базы данных для запроса и управления. 

1. Изучите данный ресурс SQL, которые вы хотите подключиться к с представлении в виде дерева.
2. Щелкните ресурс правой кнопкой мыши и выберите **Connect**, также можно найти кнопку «Подключить» в правой части ресурса.

   ![Подключение к ресурсу Azure SQL](media/azure-resource-explorer/connect-to-azure-sql-resource.png)

3. В открытой **подключения** диалоговое окно, введите пароль и нажмите кнопку **Connect**.

   ![Диалоговое окно подключения SQL](media/azure-resource-explorer/sql-connection-dialog.png)
4. **Серверы** автоматически откроется окно с помощью новой подключенной базе SQL server/после успешного подключения.

## <a name="next-steps"></a>Следующие шаги

- [Используйте [!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)] подключение и запрос базы данных Azure SQL](quickstart-sql-database.md)
- [Используйте [!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)] подключение и запрос данных в хранилище данных SQL Azure](quickstart-sql-dw.md)