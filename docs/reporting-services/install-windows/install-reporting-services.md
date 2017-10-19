---
title: "Установка SQL Server Reporting Services | Документы Microsoft"
ms.date: 10/10/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 52c2f8fae79884b025e067b7d628cd3154ba93f4
ms.openlocfilehash: 5ce83ff18d6908441a3eaaf05599068ec5876308
ms.contentlocale: ru-ru
ms.lasthandoff: 10/10/2017

---
# <a name="install-sql-server-reporting-services"></a>Установите службы SQL Server Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

Установка SQL Server Reporting Services включает в себя серверные компоненты для хранения элементов отчета, подготовки отчетов к просмотру и обработки подписок и других служб отчетов.  Дополнительные сведения об установке сервера отчетов Power BI.

Чтобы загрузить службы отчетов SQL Server 2017 г., перейдите на [центра загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=55252).

> [!NOTE]
> Ищете сервера Power BI отчетов? В разделе [Установка сервера отчетов бизнес-Аналитики Power](https://powerbi.microsoft.com/documentation/reportserver-install-report-server/).

## <a name="before-you-begin"></a>Перед началом

Перед началом установки служб Reporting Services, просмотрите [требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).

## <a name="install-your-report-server"></a>Установка сервера отчетов

Установка сервера отчетов является простой схеме. Существует всего несколько действий для установки файлов.

> [!NOTE]
> Сервер SQL Server Database Engine, доступные во время установки не обязательно. Вам потребуется для настройки служб Reporting Services после установки.

1. Найти папку SQLServerReportingServices.exe и запустить установщик.

2. Выберите **Установка служб Reporting Services**.

    ![Установка служб Reporting Services](media/install-reporting-services/report-server-install.png)

3. Выберите выпуск, чтобы установить, а затем выберите **Далее**.

    ![Выберите выпуск](media/install-reporting-services/report-server-install-edition.png)

    Вы можете Evaluation или Developer edition из раскрывающегося вниз.

    ![Evaluation или developer Edition](media/install-reporting-services/report-server-install-edition-select.png)

    В противном случае можно ввести ключ продукта.

4. Прочтите и соглашаетесь с условиями лицензии и установите **Далее**.

5. Необходимо иметь в компонент Database Engine для хранения базы данных сервера отчетов. Выберите **Далее** для установки только сервер отчетов.

    ![Не требуется для установки базы данных](media/install-reporting-services/report-server-install-db-engine.png)

6. Укажите место установки для сервера отчетов. Выберите **установить** для продолжения.

    ![Укажите путь установки](media/install-reporting-services/report-server-install-file-path.png)

    > [!NOTE]
    > Путь по умолчанию — C:\Program Files\Microsoft SQL Server Reporting Services.

7. После успешной установки, выберите **Настройка сервера отчетов** для запуска диспетчера конфигурации служб Reporting Services.

    ![Настройка сервера отчетов](media/install-reporting-services/report-server-install-configure.png)

## <a name="configuration-your-report-server"></a>Конфигурация сервера отчетов

После выбора **Настройка сервера отчетов** в программе установки, можно будет использовать с **диспетчер конфигурации сервера отчетов**. Дополнительные сведения см. в разделе [диспетчер конфигурации сервера отчетов](reporting-services-configuration-manager-native-mode.md).

Вам нужно [создать базу данных сервера отчетов](ssrs-report-server-create-a-report-server-database.md) завершения начальной настройки служб Reporting Services. Для выполнения этого шага требуется сервер базы данных SQL Server.

### <a name="creating-a-database-on-a-different-server"></a>Создание базы данных на другом сервере

При создании базы данных сервера отчетов на сервере базы данных на другом компьютере, необходимо изменить учетную запись для сервера отчетов с учетными данными, который распознается на сервере базы данных.

По умолчанию сервер отчетов использует учетную запись виртуальной службы. При попытке создать базу данных на другом сервере, может появиться следующая ошибка на этапе права применение соединения.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Чтобы устранить ошибку, можно изменить учетную запись службы для сетевой службы или учетной записью домена. Изменение учетной записи службы для сетевой службы применяет права в контексте учетной записи компьютера для сервера отчетов.

Дополнительные сведения см. в разделе [настроить учетную запись службы сервера отчетов](configure-the-report-server-service-account-ssrs-configuration-manager.md).

## <a name="windows-service"></a>Служба Windows

Службы windows создается в процессе установки. Он отображается как **SQL Server Reporting Services**. Имя службы — **SQLServerReportingServices**.

## <a name="default-url-reservations"></a>Резервирование URL-адресов по умолчанию

Резервирование URL-адреса состоит из префикса, имени узла, номера порта и имени виртуального каталога.

|Часть|Описание|
|----------|-----------------|
|Префикс|Префиксом по умолчанию является HTTP. Если ранее вы установили сертификат Secure Sockets Layer (SSL), программа установки пытается создать резервирование URL-адресов с префиксом HTTPS.|
|Имя узла|Именем узла по умолчанию является строгий шаблон (+). Указывает, что сервер отчетов принимает все HTTP-запросы по заданному порту для любого имени узла, который соответствует компьютеру, включая `http://<computername>/reportserver`, `http://localhost/reportserver`, или`http://<IPAddress>/reportserver.`|
|Порт|По умолчанию используется порт 80. Если используется порт, отличный от 80, необходимо явным образом указывать URL-адрес при открытии веб-портала в окне браузера.|
|Виртуальный каталог|По умолчанию виртуальные каталоги создаются в формате ReportServer для сервера веб-службы отчетов и отчетов для веб-портала. Для веб-службы сервера отчетов по умолчанию используется виртуальный каталог **reportserver**. Для веб-портала, виртуальный каталог по умолчанию — **отчеты**.|

Ниже приведен пример полного URL-адреса.

- `http://+:80/reportserver`, предоставляющий доступ к серверу отчетов.

- `http://+:80/reports`, предоставляет доступ к веб-портале.

## <a name="firewall"></a>Брандмауэр

При доступе к серверу отчетов с удаленного компьютера, необходимо убедиться, что вы настроили правила брандмауэра, если присутствует брандмауэр.

Необходимо открыть TCP-порт, который вы настроили для URL веб-службы и URL-адрес портала. По умолчанию они настраиваются на TCP-порт 80.

## <a name="additional-configuration"></a>Дополнительная настройка

- Чтобы настроить интеграцию со службой Power BI, вы можете закрепить элементы отчета на информационной панели Power BI, в разделе [интеграции со службой Power BI](power-bi-report-server-integration-configuration-manager.md).

- Настройке электронной почты для обработки подписок см. в разделе [параметры электронной почты,](e-mail-settings-reporting-services-native-mode-configuration-manager.md) и [доставка сервером отчетов электронной почты](../subscriptions/e-mail-delivery-in-reporting-services.md).

- Для настройки веб-портал, поэтому доступ к нему на удаленном компьютере для просмотра и управления отчетами, в разделе [настроить брандмауэр для доступа к серверу отчетов](../report-server/configure-a-firewall-for-report-server-access.md) и [настройки сервера отчетов для удаленного администрирования](../report-server/configure-a-report-server-for-remote-administration.md) .

## <a name="related-information"></a>Дополнительные сведения

Сведения о том, как установка в собственном режиме SQL Server 2016 Reporting Services см. в разделе [сервера отчетов в собственном режиме Установка служб Reporting Services](install-reporting-services-native-mode-report-server.md). Сведения об установке SQL Server 2016 Reporting Services в режиме интеграции с SharePoint см. в разделе [Установка первого сервера отчетов в режиме интеграции с SharePoint](install-the-first-report-server-in-sharepoint-mode.md).

## <a name="next-steps"></a>Следующие шаги

На сервере отчетов установлены начать создавать отчеты и разверните их на сервер отчетов. Сведения о том, как запустить с помощью построителя отчетов см. в разделе [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md).

Создание отчетов с помощью SQL Server Data Tools [скачивание SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714).

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
