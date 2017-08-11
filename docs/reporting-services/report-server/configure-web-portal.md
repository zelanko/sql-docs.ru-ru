---
title: "Настройка веб-портале | Документы Microsoft"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- the web portal [Reporting Services], configuring
ms.assetid: e918986c-af15-48f6-8178-256aed829c6a
caps.latest.revision: 28
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c0c6cc27711140e96bbf4420e8de596af53ddfcd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="configure-the-web-portal"></a>Настройка веб-портале

веб-портал является внешнего интерфейса веб-приложения используется для просмотра отчетов, управления содержимым сервера отчетов и предоставление пользователям доступа к серверу отчетов собственного режима. на веб-портале устанавливается с сервера веб-службы отчетов в пределах одного экземпляра сервера отчетов и при необходимости настраивается при выборе **установка в конфигурации собственного режима по умолчанию** в программе установки. Можно также настроить веб-портале, как задача после установки. Этот раздел содержит сведения о следующих сценариях настройки портала web:

## <a name="prerequisites"></a>Предварительные требования

Чтобы использовать веб-портале, должны быть выполнены следующие предварительные условия.

- Необходим минимально настроенный сервер отчетов. Дополнительные сведения о минимальной настройке сервера отчетов см. в разделе [настроить сервер отчетов](../../reporting-services/report-server/configure-a-report-server-reporting-services-native-mode.md).

- Сервер отчетов должен работать в собственном режиме. Веб-портала нельзя использовать с сервером отчетов, настроенный для режима интеграции с SharePoint. В SQL Server 2012 нельзя переключать сервер отчетов из одного режима в другой. Чтобы изменить тип сервера отчетов, используемый в конкретной среде, необходимо установить желаемый режим сервера отчетов, затем скопировать или переместить элементы отчетов на новый сервер отчетов. Этот процесс обычно называется миграцией. Действия, которые необходимо выполнить для миграции, зависят от режима, в котором осуществляется миграция, и версии сервера, с которого производится миграция. Дополнительные сведения см. в разделе [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).

- Вам также необходим Internet Explorer 11 или более поздней версии, с помощью сценариев включена. Дополнительные сведения см. в разделе [Поддержка браузера для служб Reporting Services и Power View](../../reporting-services/browser-support-for-reporting-services-and-power-view.md).

## <a name="configure-the-web-portal-to-use-the-default-url"></a>Настройка веб-портале использовать URL-адрес по умолчанию

Веб-портала является веб-приложения доступны пользователям через веб-браузер. Пользователь должен, по меньшей мере, задать URL-адрес для открытия приложения в окне браузера. Этот URL-адрес состоит из имени узла, порта и виртуального каталога. Применяемые по умолчанию значения для данного URL-адреса включают в себя имя узла и значения портов, которые пользователь задал для URL-адреса веб-службы сервера отчетов, плюс имя виртуального каталога **reports** . Если имеется именованный экземпляр, виртуальный каталог имеет вид **отчет_экземпляр**, где **экземпляр** — имя экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

По умолчанию веб-портале, URL-адрес состоит из уникального имени виртуального каталога, а также имени порта и главного узла, определенного для сервера веб-службы отчетов, работающей на том же экземпляре. В большинстве случаев именем узла является сетевое имя компьютера сервера отчетов, но в этом качестве может выступать и IP-адрес или заголовок узла, который разрешает компьютер. Чтобы настроить веб-портале использовать URL-адрес по умолчанию, используйте **URL-адрес портала** страницы в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] средство настройки.

> [!TIP]
> Если при попытке доступа к веб-портала на удаленном компьютере и появляется сообщение об ошибке соединения в браузере, вероятная причина — настройки брандмауэра. Дополнительные сведения см. в статье [Настройка брандмауэра для доступа к серверу отчетов](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).

#### <a name="to-configure-the-default-the-web-portal-url-and-virtual-directory"></a>Для настройки по умолчанию веб-портале URL-адрес и виртуальный каталог

1. Запустите программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и подключитесь к экземпляру сервера отчетов.

2. В [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] средство настройки, выберите **URL-адрес портала** чтобы открыть страницу для настройки URL-адрес.

3. Введите уникальное имя виртуального каталога веб-портала.

4. Нажмите кнопку **Применить**.

5. Если вы используете [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] или Windows Server 2008, дополнительные действия могут быть необходимы, прежде чем использовать веб-портале. Дополнительные сведения см. в статье [Настройка сервера отчетов, работающего в собственном режиме, для локального администрирования (SSRS)](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).

## <a name="configure-the-web-portal-to-use-a-specific-report-server-url"></a>Настройка веб-портал для использования URL-адрес определенного отчета сервера

По умолчанию веб-портале подключается к серверу веб-службы отчетов, работающего в той же службе сервера отчетов. На веб-портале использует URL-адрес службы отчетов для подключения. Если определить несколько URL-адресов для сервера веб-службы отчетов, веб-портала использует последним, которое было определено. Однако в некоторых развертываниях может потребоваться веб-портале всегда подключаются к веб-службе через статический URL-адрес. Пример подобной ситуации: пользователь настроил средства фильтрации пакетов на использование конкретного порта или IP-адреса и хочет, чтобы все соединения с сервером отчетов проходили через определенный им фильтр.

При настройке URL-адреса в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] средство настройки веб-портал автоматически обнаруживает и использует все новые и обновленные URL-адреса для сервера отчетов, который выполняется в том же экземпляре сервера. Если развертывание требует использования одного статического URL-адреса для всех запросов сервера отчетов, этот URL-адрес можно указать в файле RSReportServer.config.

#### <a name="to-configure-a-static-report-server-url"></a>Настройка статического URL-адреса сервера отчетов

1. Откройте файл **RSReportServer.config** в текстовом редакторе. По умолчанию он находится в \Program Files\Microsoft SQL Server\MSRS12. \< *instancename*> \Reporting Services\ReportServer.  

2. Найдите параметр **ReportServerURL**.

3. Замените его URL-адресом экземпляра сервера отчетов.

4. Сохраните внесенные изменения и закройте файл.

Дополнительные сведения о местоположении и изменении файлов конфигурации см. в разделах [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) и [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).

## <a name="customize-styles-or-application-title"></a>Настройка стилей или заголовка приложения

Можно создать пакет пользовательской фирменной символики для изменения цвета, используемые для веб-портала. Дополнительные сведения см. в разделе [фирменная символика на веб-портале](../branding-the-web-portal.md)

#### <a name="to-modify-application-title"></a>Изменение заголовка приложения

1. Войдите в систему с учетной записью **Системный администратор** , имеющей разрешения на работу с сервером отчетов.

2. Откройте обозреватель Internet Explorer.

3. Введите веб-портале URL-адрес. По умолчанию это http://\<**your server name**> / reports, но, если службы Reporting Services установлены как именованный экземпляр, URL-адрес по умолчанию будет http://\<**your server name**> / reports\<**_имяэкземпляра**>.

4. Выберите пункт **Настройки сайта**.

5. На вкладке **Общие** в поле **Имя**замените имя **SQL Server Reporting Services** другим именем.

6. Нажмите кнопку **Применить**.

## <a name="next-steps"></a>Следующие шаги

[Веб-портал](../../reporting-services/web-portal-ssrs-native-mode.md)  
[Поддержка браузеров для служб Reporting Services](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)
[настроить URL-адрес](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
[Проверка установки служб Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
[Включение и отключение компонентов служб Reporting Services](../../reporting-services/report-server/turn-reporting-services-features-on-or-off.md)   
[Управление сервером отчетов служб Reporting Services в собственном режиме](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)   
[Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[Настройка сервера отчетов в собственном режиме для локального администрирования](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)

 Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
