---
title: Просмотр ресурсов SQL Azure с помощью обозреватель ресурсов Azure
description: Сведения о том, как просматривать Azure SQL Server, базу данных SQL Azure и Управляемый экземпляр Azure SQL и управлять ими с помощью обозревателя ресурсов Azure.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: yanancai
ms.author: yanacai
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 5b4081d98a30daa61a1e10ecf4faa6000a0fe11c
ms.sourcegitcommit: 63aef5a96905f0b026322abc9ccb862ee497eebe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "91364164"
---
# <a name="explore-and-manage-azure-sql-resources-with-azure-resource-explorer"></a>Просмотр ресурсов SQL Azure и управление ими с помощью обозревателя ресурсов Azure

Этот документ описывает, как просматривать ресурсы Azure SQL Server, базы данных SQL Azure и Управляемого экземпляра Azure SQL и управлять ими с помощью обозревателя ресурсов Azure в [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)].

>[!NOTE]
>Обозреватель ресурсов Azure поддерживается в SQL Server 2019. После этого вы сможете установить расширение с помощью [диспетчера расширений](extensions.md) или команды **Файл** > **Установить пакет из пакета VSIX**.

## <a name="connect-to-azure"></a>Подключение к Azure

После установки подключаемого модуля SQL в левой строке меню появится значок Azure. Щелкните его, чтобы открыть обозреватель ресурсов Azure. Если вы не видите значок Azure, щелкните правой кнопкой мыши в левой строке меню и выберите **Обозреватель ресурсов Azure**.

### <a name="add-an-azure-account"></a>Добавление учетной записи Azure

Чтобы просмотреть ресурсы SQL, связанные с учетной записью Azure, нужно сначала добавить учетную запись в [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)].

1. Откройте диалоговое окно **Связанные учетные записи** с помощью значка управления учетной записью в левом нижнем углу или ссылки **Войти в Azure...** в обозревателе ресурсов Azure.

    ![Вход в Azure](media/azure-resource-explorer/sign-in-to-azure.png)

2. В диалоговом окне **Связанные учетные записи** щелкните **Добавить учетную запись**.

    ![Добавление учетной записи Azure](media/azure-resource-explorer/add-an-azure-account.png)

3. Щелкните **Копировать и открыть**, чтобы открыть браузер для проверки подлинности.

    ![Открытие страницы проверки подлинности в браузере](media/azure-resource-explorer/open-authentication-in-browser.png)

4. Вставьте **Пользовательский код** на веб-страницу и нажмите кнопку **Продолжить** для проверки подлинности.

    ![Проверка подлинности в браузере](media/azure-resource-explorer/authenticate-in-browser.png)

5. В [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)] учетная запись Azure, с помощью которой был выполнен вход, теперь должна отображаться в диалоговом окне **Связанные учетные записи**.

    ![Учетная запись Azure вошедшего пользователя](media/azure-resource-explorer/signed-in-azure-account.png)

### <a name="add-more-azure-accounts"></a>Добавление дополнительных учетных записей Azure

В [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)] поддерживается несколько учетных записей Azure. Чтобы добавить дополнительные учетные записи Azure, нажмите кнопку в правой верхней части диалогового окна **Связанные учетные записи** и выполните те же действия, которые описаны в разделе "Добавление учетной записи Azure".

![Добавление дополнительной учетной записи Azure](media/azure-resource-explorer/add-more-azure-account.png)

### <a name="remove-an-azure-account"></a>Удаление учетной записи Azure

Чтобы удалить существующую учетную запись Azure пользователя, выполнившего вход, сделайте следующее.

1. Откройте диалоговое окно **Связанные учетные записи** с помощью значка управления учетной записью в левом нижнем углу.
2. Нажмите кнопку **X** справа от учетной записи Azure, чтобы удалить ее.

    ![Удаление учетной записи Azure](media/azure-resource-explorer/remove-azure-account.png)

## <a name="filter-subscription"></a>Фильтрация подписок

После входа в учетную запись Azure в обозревателе ресурсов Azure отображаются все связанные с ней подписки. Вы можете отфильтровать их для каждой учетной записи Azure.

1. Нажмите кнопку **Выбрать подписку** справа от учетной записи Azure.

   ![Фильтрация подписок](media/azure-resource-explorer/filter-subscription.png)

2. Установите флажки для подписок учетной записи, которые требуется просмотреть, и нажмите кнопку **ОК**.

   ![Выбор подписки](media/azure-resource-explorer/select-subscription.png)

## <a name="explore-azure-sql-resources"></a>Просмотр ресурсов SQL Azure

Для перемещения по ресурсам SQL Azure в обозревателе ресурсов Azure разверните группу учетных записей Azure и типов ресурсов.

Сейчас обозреватель ресурсов Azure поддерживает Azure SQL Server, базу данных SQL Azure и Управляемый экземпляр SQL Azure.

## <a name="connect-to-azure-sql-resources"></a>Подключение к ресурсам SQL Azure

Обозреватель ресурсов Azure обеспечивают быстрый доступ, позволяя подключаться к серверам и базам данных SQL для выполнения запросов и управления.

1. Изучите ресурс SQL, к которому вы хотите подключиться, из представления в виде дерева.
2. Щелкните ресурс правой кнопкой мыши и выберите пункт **Подключить**. Кроме того, можно использовать кнопку подключения справа от ресурса.

   ![Подключение к ресурсу SQL Azure](media/azure-resource-explorer/connect-to-azure-sql-resource.png)

3. В открывшемся диалоговом окне **Подключение** введите свой пароль и нажмите кнопку **Подключить**.

   ![Диалоговое окно подключения SQL](media/azure-resource-explorer/sql-connection-dialog.png)
4. После установки подключения автоматически открывается окно **Серверы** с новым подключенным сервером или базой данных SQL.

## <a name="next-steps"></a>Дальнейшие действия

- [Использование [!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)] для подключения и отправки запроса к базе данных SQL Azure](quickstart-sql-database.md)
- [Подключение к Хранилищу данных SQL Azure и запрос данных с помощью [!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)]](quickstart-sql-dw.md)