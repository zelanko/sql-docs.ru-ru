---
description: URL-адреса в файлах конфигурации (диспетчер конфигурации сервера отчетов)
title: URL-адреса в файлах конфигурации (диспетчер конфигурации) | Документация Майкрософт
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL configuration [Reporting Services]
ms.assetid: 4f5e7fe0-b5b1-4665-93d4-80dce12d6b14
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 17eaa59595b8a35fe1d9aa7fa3c69e6d0b39860f
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91934504"
---
# <a name="urls-in-configuration-files--report-server-configuration-manager"></a>URL-адреса в файлах конфигурации (диспетчер конфигурации сервера отчетов)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] сохраняют параметры приложений в файле RSReportServer.config. В этом файле содержатся как URL-адреса, так и резервирование URL-адресов. Эти параметры имеют различные предназначения и подчиняются различным правилам изменения. Пользователям, имеющим опыт изменения настройки системы через файлы конфигурации, этот раздел поможет узнать назначение каждого из параметров URL-адресов.  
  
## <a name="url-settings-in-rsreportserverconfig-file"></a>Параметры URL-адресов в файле RSReportServer.config  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] сохраняет URL-адреса для доступа к приложениям и отчетам, а также для соединения клиентских веб-компонентов с сервером отчетов.  
  
#### <a name="urls-for-application-access"></a>URL-адреса для доступа к приложениям  
 URL-адреса используются для доступа к веб-службам сервера отчетов и [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]. Для их настройки необходимо пользоваться программой настройки служб Reporting Services. Эта программа создает для каждого из приложений резервирование URL-адресов в компоненте HTTP.SYS и добавляет соответствующие записи в раздел **URLReservations** файла RSReportServer.config.  
  
-   Описания каждого элемента в разделе **URLReservations** см. в статье [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).  
  
-   Дополнительные сведения о синтаксисе элемента **UrlString** см. в статье [Синтаксис резервирования URL-адресов (диспетчер конфигурации сервера отчетов)](../../reporting-services/install-windows/url-reservation-syntax-ssrs-configuration-manager.md).  
  
-   Инструкции по настройке URL-адресов для доступа к приложениям см. в статье [Настройка URL-адреса (диспетчер конфигурации сервера отчетов)](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
#### <a name="urls-for-report-access"></a>URL-адреса для доступа к отчетам  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включает модуль доставки по электронной почте, который можно использовать для рассылки отчетов в виде ссылок или вложений. Ссылка на отчет формируется в момент его доставки. Ее формирование производится модулем доставки электронной почты сервера отчетов в соответствии с параметром **UrlRoot** в файле конфигурации. Кроме того, параметр**UrlRoot** используется при разрешении ссылок в отчете, готовом для просмотра, созданном в процессе автоматической обработки.  
  
 Параметр**UrlRoot** автоматически задается в файле RSReportServer.config при настройке URL-адресов для доступа к приложениям. Изменяя это значение в файле конфигурации, необходимо указывать действительный URL-адрес веб-службы сервера отчетов, которая подключена к базе данных сервера отчетов, в которой содержатся доставляемые отчеты. Параметр **UrlRoot** может быть указан только для одного экземпляра сервера отчетов. Для каждого экземпляра сервера отчетов в файле RSReportServer.config может существовать только одна запись **UrlRoot** . Если веб-службой сервера отчетов зарезервировано несколько URL-адресов, то в качестве значения параметра **UrlRoot**должно быть выбрано одно из доступных значений.  
  
 В большинстве случаев изменение параметра **UrlRoot**не требуется. Но если планируется доступ к серверу отчетов по полному URL-адресу, а для заголовка сайта не задан URL-адрес, содержащий его полное имя, нужно вручную изменить файл RSReportServer.config, задав в параметре **UrlRoot** полный URL-адрес сервера отчетов, который будет использоваться при подготовке отчетов (например, `https://www.adventure-works.com/mywebapp/reportserver`).  
  
#### <a name="urls-connecting-the-ssrswebportal-and-web-parts-to-the-report-server-web-service"></a>URL-адреса для соединения [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] и веб-частей с веб-службами сервера отчетов  
 [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] и веб-части SharePoint 2.0 для служб Reporting Services представляют собой клиентские веб-части, подключаемые к серверу отчетов. Для соединения с сервером отчетов используются следующие URL-адреса.  
  
-   **ReportServerUrl** (используется [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)])  
  
-   **ReportServerExternalUrl** (используется веб-частями)  
  
> [!NOTE]  
>  Предыдущие версии служб Reporting Services включали элемент **ReportServerVirtualDirectory** . В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях это значение является устаревшим. Если после обновления существующей установки остался файл конфигурации, содержащий этот параметр, то сервер отчетов его считывание не производит.  
  
 В следующей таблице кратко перечислены все URL-адреса, которые могут быть заданы в файле конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
|Параметр|Использование|Описание|  
|-------------|-----------|-----------------|  
|**ReportServerUrl**|Необязательный параметр. Этот элемент отсутствует в файле конфигурации RSReportServer.config, его необходимо добавить вручную.<br /><br /> Этот элемент задается только при настройке по одному из следующих сценариев.<br /><br /> [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] предоставляет клиентский доступ к веб-службам сервера отчетов, работающих на другом компьютере или другом экземпляре на том же компьютере.<br /><br /> Если сервер отчетов имеет несколько URL-адресов, а [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] должен быть доступен по конкретному URL-адресу.<br /><br /> Существует конкретный URL-адрес сервера отчетов, по которому должны производиться все соединения [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] .<br /><br /> Например, можно разрешить доступ к [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] для всех компьютеров в сети, но потребовать, чтобы [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] соединялся с сервером отчетов по локальному соединению. В этом случае можно указать для параметра **ReportServerUrl** значение "`https://localhost/reportserver`".|Это значение указывает URL-адрес веб-службы сервера отчетов. Это значение считывается приложением [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] при запуске. Если значение задано, [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] соединяется с сервером отчетов, указанным в URL-адресе.<br /><br /> По умолчанию [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] обеспечивает доступ клиентов к веб-службе сервера отчетов, работающей на том же экземпляре сервера отчетов, что и [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]. Однако если необходимо использовать [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] совместно с веб-службой сервера отчетов, который является частью другого экземпляра или работает на другом компьютере, то можно указать его URL-адрес, чтобы [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] соединялся с внешними веб-службами сервера отчетов.<br /><br /> Если на сервере отчетов, с которым проводится соединение, установлен сертификат TLS (ранее — SSL), то параметр **ReportServerUrl** должен содержать имя сервера, зарегистрированного для данного сертификата. Если возникло сообщение об ошибке "Базовое соединение закрыто: не удалось установить отношение доверия для безопасного канала SSL/TLS", задайте в качестве значения параметра **ReportServerUrl** полное доменное имя сервера, для которого был выдан сертификат TLS/SSL. Например, если сертификат был зарегистрирован для **https:\//adventure-works.com.onlinesales**, в качестве URL-адреса сервера отчетов будет использоваться **https:\//adventure-works.com.onlinesales/reportserver**.|  
|**ReportServerExternalUrl**|Необязательный параметр. Этот элемент отсутствует в файле конфигурации RSReportServer.config, его необходимо добавить вручную.<br /><br /> Этот элемент следует указывать только при использовании веб-частей SharePoint 2.0, если необходимо предоставлять пользователям возможность получения и открытия отчетов в новом окне браузера.<br /><br /> Внутри элемента \<**ReportServerUrl**> добавьте элемент \<**ReportServerExternalUrl**>, указав в нем полное имя сервера отчетов, которое разрешается до экземпляра сервера отчетов при обращении из отдельного окна браузера. Не удаляйте \<**ReportServerUrl**>.<br /><br /> В следующем примере показан синтаксис:<br /><br /> `<ReportServerExternalUrl>https://myserver/reportserver</ReportServerExternalUrl>`|Это значение используется веб-частями SharePoint 2.0.<br /><br /> В предыдущих версиях это значение рекомендовалось задавать при развертывании построителя отчетов на сервере отчетов, доступном из Интернета. Этот сценарий развертывания не тестировался. Если в прошлом этот параметр использовался для поддержки доступа к построителю отчетов через Интернет, следует рассмотреть альтернативную стратегию.|  
  
## <a name="see-also"></a>См. также:  
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации сервера отчетов)](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Настройка URL-адреса (диспетчер конфигурации сервера отчетов)](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)
