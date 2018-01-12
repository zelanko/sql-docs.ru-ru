---
title: "Установка служб SQL Server Reporting Services (2017 или более поздней версии) | Документы Майкрософт"
ms.date: 12/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Active
ms.openlocfilehash: 2f09b475d42657c8c9ce8ef60d6b5b7c36b30cc2
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="install-sql-server-reporting-services-2017-and-later"></a>Установка служб SQL Server Reporting Services (2017 или более поздней версии)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

Установка служб SQL Server Reporting Services включает в себя серверные компоненты для хранения элементов отчета, подготовки отчетов к просмотру, а также для обработки подписок и других служб отчетов. 

Чтобы скачать службы Microsoft SQL Server 2017 Reporting Services, перейдите в [Центр загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=55252).

> [!NOTE]
> Ищете сервер отчетов Power BI? См. раздел [Установка сервера отчетов Power BI](https://powerbi.microsoft.com/documentation/reportserver-install-report-server/).

## <a name="before-you-begin"></a>Перед началом

Перед установкой служб Reporting Services ознакомьтесь с [требованиями к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).

## <a name="install-your-report-server"></a>Установка сервера отчетов

Установка сервера отчетов не вызывает никаких трудностей. Нужно выполнить лишь несколько действий по установке файлов.

> [!NOTE]
> Во время установки вам не потребуется сервер ядра СУБД SQL Server. Он будет нужен для настройки служб Reporting Services после установки.

1. Найдите папку с файлом SQLServerReportingServices.exe и запустите установщик.

2. Выберите **Установка служб Reporting Services**.

    ![Установка служб Reporting Services](media/install-reporting-services/report-server-install.png)

3. Выберите устанавливаемый выпуск, а затем нажмите кнопку **Далее**.

    ![Выбор выпуска](media/install-reporting-services/report-server-install-edition.png)

    Для бесплатного выпуска в раскрывающемся списке выберите выпуск Evaluation или Developer.

    ![Выпуск Evaluation или Developer](media/install-reporting-services/report-server-install-edition-select.png)

    В противном случае введите ключ продукта. [Как найти ключ продукта для SQL Server Reporting Services 2017](find-reporting-services-product-key-ssrs.md)

4. Прочтите и примите условия лицензионного соглашения, а затем нажмите кнопку **Далее**.

5. Для хранения базы данных сервера отчетов вам потребуется ядро СУБД. Нажмите кнопку **Далее**, чтобы установить только сервер отчетов.

    ![Устанавливать базу данных не требуется](media/install-reporting-services/report-server-install-db-engine.png)

6. Укажите расположение установки для сервера отчетов. Чтобы продолжить, нажмите кнопку **Установить**.

    ![Укажите путь установки](media/install-reporting-services/report-server-install-file-path.png)

    > [!NOTE]
    > По умолчанию установка производится в каталог C:\Program Files\Microsoft SQL Server Reporting Services.

7. После успешной установки нажмите кнопку **Настроить сервер отчетов**, чтобы запустить диспетчер конфигурации служб Reporting Services.

    ![Настроить сервер отчетов](media/install-reporting-services/report-server-install-configure.png)

## <a name="configuration-your-report-server"></a>Настройка вашего сервера отчетов

После нажатия кнопки **Настроить сервер отчетов** в программе установки откроется **Диспетчер конфигурации сервера отчетов**. Дополнительные сведения см. в разделе [Диспетчер конфигурации сервера отчетов](reporting-services-configuration-manager-native-mode.md).

Для завершения начальной настройки служб Reporting Services нужно [создать базу данных сервера отчетов](ssrs-report-server-create-a-report-server-database.md). Для выполнения этого шага требуется сервер базы данных SQL Server.

### <a name="creating-a-database-on-a-different-server"></a>Создание базы данных на другом сервере

Если база данных сервера отчетов создается на сервере базы данных на другом компьютере, необходимо изменить учетную запись для сервера отчетов на учетные данные, которые распознаются на сервере базы данных.

По умолчанию сервер отчетов использует учетную запись виртуальной службы. При попытке создать базу данных на другом сервере на этапе применения прав на соединение может появиться следующая ошибка.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Чтобы устранить ее, измените учетную запись службы на учетную запись сетевой службы или учетную запись домена. При изменении учетной записи службы на учетную запись сетевой службы к серверу отчетов применяются права в контексте учетной записи компьютера.

Дополнительные сведения см. в разделе [Настройка учетной записи службы сервера отчетов](configure-the-report-server-service-account-ssrs-configuration-manager.md).

## <a name="windows-service"></a>Служба Windows

Служба Windows создается в процессе установки. Она отображается как **SQL Server Reporting Services**. Имя службы — **SQLServerReportingServices**.

## <a name="default-url-reservations"></a>Резервирование URL-адресов по умолчанию

Резервирование URL-адреса состоит из префикса, имени узла, номера порта и имени виртуального каталога.

|Часть|Description|
|----------|-----------------|
|Prefix|Префиксом по умолчанию является HTTP. Если сертификат SSL уже установлен, программа установки попытается создать резервирование URL-адресов с префиксом HTTPS.|
|Имя узла|Именем узла по умолчанию является строгий шаблон (+). Он указывает, что сервер отчетов принимает все HTTP-запросы в заданном порте для любого имени узла, который соответствует компьютеру, включая `http://<computername>/reportserver`, `http://localhost/reportserver` или `http://<IPAddress>/reportserver.`|
|Порт|По умолчанию используется порт 80. Если используется порт, отличный от 80, то его необходимо явным образом указывать в URL-адресе при открытии веб-портала в окне браузера.|
|Виртуальный каталог|По умолчанию имена виртуальных каталогов создаются в формате ReportServer — для веб-службы сервера отчетов и в формате Reports — для диспетчера отчетов. Для веб-службы сервера отчетов по умолчанию используется виртуальный каталог **reportserver**. Для веб-портала используется виртуальный каталог по умолчанию **reports**.|

Ниже приведен пример полного URL-адреса.

- `http://+:80/reportserver`, предоставляет доступ к серверу отчетов.

- `http://+:80/reports`, предоставляет доступ к веб-порталу.

## <a name="firewall"></a>Брандмауэр

Если доступ к серверу отчетов осуществляется с удаленного компьютера, должны быть настроены правила брандмауэра, если имеется брандмауэр.

Необходимо открыть TCP-порт, который настроен для URL-адреса веб-службы и URL-адреса веб-портала. По умолчанию они настроены на TCP-порте 80.

## <a name="additional-configuration"></a>Дополнительная настройка

- Чтобы настроить интеграцию со службой Power BI и закреплять элементы отчета на панели мониторинга Power BI, см. сведения в разделе [Интеграция со службой Power BI](power-bi-report-server-integration-configuration-manager.md).

- Сведения о настройке электронной почты для обработки подписок см. в разделах [Настройки электронной почты](e-mail-settings-reporting-services-native-mode-configuration-manager.md) и [Доставка электронной почты на сервере отчетов](../subscriptions/e-mail-delivery-in-reporting-services.md).

- Инструкции по настройке веб-портала для просмотра отчетов и управления ими с удаленного компьютера см. в статьях [Настройка брандмауэра для доступа к серверу отчетов](../report-server/configure-a-firewall-for-report-server-access.md) и [Настройка сервера отчетов для удаленного администрирования](../report-server/configure-a-report-server-for-remote-administration.md).

## <a name="related-information"></a>Дополнительные сведения

Сведения об установке служб SQL Server 2016 Reporting Services см. в разделе [Установка сервера отчетов служб Reporting Services в собственном режиме](install-reporting-services-native-mode-report-server.md). Сведения об установке SQL Server 2016 Reporting Services в режиме интеграции с SharePoint см. в разделе [Установка первого сервера отчетов в режиме интеграции с SharePoint](install-the-first-report-server-in-sharepoint-mode.md).

## <a name="next-steps"></a>Следующие шаги

После установки сервера отчетов можно приступить к созданию отчетов и их развертыванию на сервере отчетов. Сведения о начале работы с построителем отчетов см. в разделе [Установка построителя отчетов](../../reporting-services/install-windows/install-report-builder.md).

Чтобы создавать отчеты с помощью SQL Server Data Tools, [скачайте SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714).

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
