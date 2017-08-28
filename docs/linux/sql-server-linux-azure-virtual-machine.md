---
title: "Подготовьте Linux SQL Server виртуальную Машину в Azure | Документы Microsoft"
description: "Этого учебника показано, как создать виртуальную машину 2017 г. Linux SQL Server в Azure."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 222e23b2-51e7-429b-b8e5-61e0ebe7df9b
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 0470622b0fe5a8835213617a4fc2e8c74f674873
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-linux-sql-server-2017-virtual-machine-with-the-azure-portal"></a>Создание виртуальной машины Linux SQL Server, 2017 г. с помощью портала Azure

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Azure предоставляет образы виртуальных машин Linux, имеющих установлен SQL Server 2017 г RC2. В этом разделе предоставляет краткое Пошаговое руководство по использованию портала Azure для создания виртуальной машины с Linux SQL Server. 

## <a name="create-a-linux-vm-with-sql-server-installed"></a>Создайте виртуальную Машину Linux с установленным сервером SQL Server

Откройте [портал Azure](https://portal.azure.com/).

1. Нажмите кнопку **New** в левой части экрана.

1. В **New** колонка, щелкните **вычислений**.

1. Нажмите кнопку **разделе все** рядом с **популярные приложения** заголовок.

   ![Все образы виртуальных Машин см.](./media/sql-server-linux-azure-virtual-machine/azure-compute-blade.png)

1. В поле поиска введите **2017 г. SQL Server**и нажмите клавишу **ввод** следует начать поиск.

    ![Фильтр поиска для образов виртуальной Машины SQL Server 2017 г.](./media/sql-server-linux-azure-virtual-machine/searchfilter.png)

    > [!TIP]
    > Отображаются доступные образы виртуальных машин Linux 2017 г. SQL Server. Со временем будут перечислены изображений 2017 г. SQL Server для других поддерживаемых дистрибутивах Linux. Можно также щелкнуть [ссылку](https://ms.portal.azure.com/#blade/Microsoft_Azure_Marketplace/GalleryFeaturedMenuItemBlade/selectedMenuItemId/home/searchQuery/sql%20server%202017) чтобы перейти непосредственно к результатам поиска для 2017 г. SQL Server. 

1. Выберите образ 2017 г. SQL Server в результатах поиска.

1. Нажмите кнопку **Создать**.

1. На **основы** колонки, заполните сведения для ВМ Linux. 

    ![Основы колонку](./media/sql-server-linux-azure-virtual-machine/basics.png)

    > [!Note]
    > Вы можете выбрать использование открытый ключ SSH или пароль для проверки подлинности. SSH является более безопасным. Инструкции по созданию ключа SSH. в разделе [создать SSH ключи на Mac и Linux для виртуальных машин Linux в Azure](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-mac-create-ssh-keys). 

1. Нажмите кнопку **ОК**.

1. На **размер** колонке выберите размер машины. Для разработки и функциональное тестирование, рекомендуется размер виртуальной Машины **DS2** или более поздней версии. Для тестирования производительности, используйте **DS13** или более поздней версии.

    ![Выберите размер виртуальной Машины](./media/sql-server-linux-azure-virtual-machine/vmsizes.png)

    Для просмотра других размеров, выберите **просмотреть все**. Дополнительные сведения о размерах виртуальных Машин машины см. в разделе [размеры виртуальных Машин Linux](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-sizes).

1. Нажмите кнопку **Выбрать**.

1. На **параметры** колонки, можно внести изменения в параметры или сохранить параметры по умолчанию.

1. Нажмите кнопку **ОК**.

1. На **Сводка** щелкните **ОК** для создания виртуальной Машины.

> [!NOTE]
> Виртуальная машина Azure предварительно настраивает брандмауэр так, чтобы открыть SQL Server порт 1433 для удаленных соединений. Но чтобы удаленно подключиться, необходимо также добавить правило группы безопасности сети, как описано в следующем разделе.

## <a id="remote"></a>Настройка для удаленных подключений

Чтобы иметь возможность удаленно подключиться к SQL Server на Виртуальной машине Azure, необходимо настроить правило входящего трафика на группу безопасности сети. Правило разрешает трафик через порт, который SQL Server прослушивает (по умолчанию 1433). Ниже показано, как использовать портал Azure для выполнения этого шага. 

1. На портале выберите **виртуальные машины**и выберите Машину SQL Server.

1. В списке свойств выберите **сетевых интерфейсов**.

1. Затем выберите сетевой интерфейс для виртуальной Машины.

    ![Сетевые интерфейсы](./media/sql-server-linux-azure-virtual-machine/networkinterfaces.png)

1. Щелкните ссылку группы безопасности сети.

    ![Группы безопасности сети](./media/sql-server-linux-azure-virtual-machine/networksecuritygroup.png)

1. В свойствах группы безопасности сети, selct **безопасности правила для входящих подключений**.

1. Нажмите кнопку **+ добавить** кнопки.

1. Введите имя «SQLServerRemoteConnections».

1. В **службы** выберите **MS SQL**.

    ![Правило группы безопасности MS SQL](./media/sql-server-linux-azure-virtual-machine/sqlnsgrule.png)

1. Нажмите кнопку **ОК** чтобы сохранить правило для виртуальной Машины.

## <a id="connect"></a>Подключитесь к виртуальной Машине Linux

Если вы уже используете оболочке BASH, подключения к виртуальной Машине Azure с помощью **ssh** команды. В следующей команде замените имя пользователя виртуальной Машины и IP-адрес для подключения к виртуальной Машине Linux.

```bash
ssh -l AzureAdmin 100.55.555.555
```

IP-адрес виртуальной Машины можно найти на портале Azure.

![IP-адрес на портале Azure](./media/sql-server-linux-azure-virtual-machine/vmproperties.png)

Если запущены на Windows и не имеют оболочки BASH, можно установить клиент SSH, например PuTTY.

1. [Загрузите и установите PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

1. Запустите PuTTY.

1. На экране настройки PuTTY введите общедоступный IP-адрес Виртуальной машины.

1. Щелкните "Открыть" и введите имя пользователя и пароль на экране.

Дополнительные сведения о подключении к виртуальным машинам Linux см. в разделе [Создание виртуальной Машины Linux в Azure, с помощью портала](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-quick-create-portal#ssh-to-the-vm).

## <a name="configure-sql-server"></a>Настройте SQL Server

1. После подключения к виртуальной Машине Linux, откройте новую команду терминалов.

1. Установка SQL Server с помощью следующей команды.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup 
   ```

   Примите условия лицензии и ввести пароль для учетной записи системного администратора. Можно запустить сервер при появлении запроса.

1. При необходимости [установите средства SQL Server](sql-server-linux-setup-tools.md).

## <a name="next-steps"></a>Следующие шаги

Теперь, когда виртуальная машина 2017 г. SQL Server в Azure можно подключить локально к **sqlcmd** для выполнения запросов Transact-SQL.

Если вы настроили ВМ Azure для удаленных соединений SQL Server, также можно выполнить удаленное подключение. Пример подключения к SQL Server в Linux с удаленного компьютера Windows см. в разделе [используйте SSMS в Windows для подключения к SQL Server в Linux](sql-server-linux-develop-use-ssms.md).

Дополнительные общие сведения о виртуальных машинах Linux в Azure см. в разделе [документации виртуальной машины Linux](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/).

