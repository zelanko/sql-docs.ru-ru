---
title: "Установка сервера отчетов служб Reporting Services в собственном режиме | Документы Майкрософт"
ms.custom: 
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: pro-bi
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- default configuration [Reporting Services]
- report servers [Reporting Services], default configurations
- installation options [Reporting Services]
ms.assetid: 8f25e6dc-b753-400e-9e9a-50f4f35bf6c4
caps.latest.revision: "68"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Active
ms.openlocfilehash: 9feeb8c3f7e9d2c1d365e8d6ad7f327e20d80b4f
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="install-reporting-services-native-mode-report-server"></a>Установка сервера отчетов служб Reporting Services в основном режиме

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

Сведения об установке [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме. Это обеспечит доступ к [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] , где можно управлять отчетами и другими элементами.

> [!NOTE]
> Ищете сервер отчетов Power BI? См. раздел [Установка сервера отчетов Power BI](https://powerbi.microsoft.com/documentation/reportserver-install-report-server/).

Работающий в основном режиме сервер отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — это сервер [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме по умолчанию, который можно установить с помощью мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или из командной строки. В мастере установки можно выбрать либо установку файлов и настройку сервера с параметрами по умолчанию, либо только установку файлов. В этом разделе описывается *конфигурация по умолчанию для собственного режима* , при которой программа установки устанавливает и настраивает экземпляр сервера отчетов. Когда установка будет завершена, сервер отчетов будет запущен и готов для использования базовых функций просмотра отчетов и управления отчетами.  Чтобы использовать дополнительные возможности, включая функции интеграции с [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] и доставки электронной почты с обработкой подписки, нужна дополнительная настройка.  
  
##  <a name="bkmk_whatisdefaultconfiguration"></a> Что такое конфигурация по умолчанию?  
 При выборе конфигурации по умолчанию для собственного режима программой установки устанавливаются следующие компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
-   Служба сервера отчетов (в состав которой входит веб-служба сервера отчетов, приложение фоновой обработки и [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] ) для просмотра отчетов и разрешений, а также управления ими.  
  
-   Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   Программы командной строки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (rsconfig.exe, rskeymgmt.exe и rs.exe).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] теперь загружаются отдельно.  
  
 В процессе установки сервера отчетов, работающего в собственном режиме, программой установки настраиваются следующие параметры.  
  
-   Учетная запись службы для службы сервера отчетов.  
  
-   URL-адрес веб-службы сервера отчетов.  
  
-   URL-адрес [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] .  
  
-   База данных сервера отчетов.  
  
-   Доступ учетной записи службы к базам данных сервера отчетов.  
  
-   Сведения о подключении (так называемый источник данных или DSN) для баз данных сервера отчетов.  
  
 Программа установки не производит настройку учетной записи автоматического выполнения, электронной почты сервера отчетов, резервного копирования ключей шифрования и масштабного развертывания. Для настройки этих свойств вы можете использовать диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).
  
##  <a name="bkmk_whentoinstalldefaultconfig"></a> Ситуации, требующие установки конфигурации по умолчанию для основного режима  
 При конфигурации по умолчанию службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] устанавливаются в рабочее состояние, и сервер отчетов можно использовать сразу после завершения программы установки. Выберите этот режим, чтобы сократить количество шагов и пропустить выполнение задач настройки, которые в противном случае пришлось бы выполнять в средстве настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Установка конфигурации по умолчанию не гарантирует, что сервер отчетов будет работать после завершения программы установки. Регистрация URL-адресов по умолчанию может завершиться ошибкой при запуске службы. Всегда тестируйте установку, чтобы убедиться, что служба запускается и выполняется правильно.  См. раздел [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).
  
##  <a name="bkmk_requirements"></a> Требования  
 Этот режим настройки для задания основных параметров, необходимых для приведения сервера отчетов в рабочее состояние, использует параметры конфигурации по умолчанию. К нему предъявляются следующие требования.  
  
-   См. статью [Hardware and Software Requirements for Installing SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md) .  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] должны устанавливаться на одном и том же экземпляре. Экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] размещает базу данных сервера отчетов, которую создает и настраивает программа установки.  
  
-   Учетная запись пользователя, использованная для выполнения программы установки, должна быть членом локальной группы администраторов. Кроме того, она должна обладать разрешениями для доступа и создания баз данных в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором размещены базы данных сервера отчетов.  
  
-   Программа установки должна иметь возможность использовать значения по умолчанию, чтобы резервировать URL-адреса, которые обеспечивают доступ к серверу и [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]. Этими значениями являются порт 80, строгий подстановочный знак и имена виртуальных каталогов в формате **ReportServer_\<***имя_экземпляра***>** и **Reports_\<***имя_экземпляра***>**.  
  
-   Программа установки должна иметь возможность создания баз данных сервера отчетов с использованием значений по умолчанию. Это значения **ReportServer** и **ReportServerTempDB**. Если от предыдущей установки остались базы данных, то программа установки будет заблокирована, поскольку она не сможет настроить сервер отчетов в конфигурации по умолчанию для собственного режима. Чтобы снять блокировку программы установки, следует переименовать, переместить или удалить базы данных.  
  
 Если компьютер не отвечает всем требованиям для установки по умолчанию, нужно установить службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме «только файлы», а после установки настроить компьютер с помощью диспетчера настройки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .
 
 > [!IMPORTANT]
 > Хотя службы Reporting Services можно установить в среде с контроллером домена только для чтения (RODC), для правильной работы служб Reporting Services им требуется доступ к контроллеру домена для чтения и записи. Если у служб Reporting Services есть доступ только к контроллеру домена только для чтения, при попытке управления ими могут возникать ошибки.
  
##  <a name="bkmk_defaultURLreservations"></a> Резервирование URL-адресов по умолчанию  
 Резервирование URL-адреса состоит из префикса, имени узла, номера порта и имени виртуального каталога.  
  
|Часть|Описание|  
|----------|-----------------|  
|Префикс|Префиксом по умолчанию является HTTP. Если сертификат SSL уже установлен, программа установки попытается создать резервирование URL-адресов с префиксом HTTPS.|  
|Имя узла|Именем узла по умолчанию является строгий шаблон (+). Он указывает, что сервер отчетов принимает все HTTP-запросы в заданном порте для любого имени узла, который соответствует компьютеру, включая `http://<computername>/reportserver`, `http://localhost/reportserver` или `http://<IPAddress>/reportserver`|  
|Порт|По умолчанию используется порт 80. Следует иметь в виду, что если используется порт, отличный от 80, то его необходимо явным образом указывать в URL-адресе при открытии веб-приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в окне браузера.|  
|Виртуальный каталог|По умолчанию имена виртуальных каталогов формируются по модели ReportServer_\<*имя_экземпляра*> для веб-службы сервера отчетов и по модели Reports_\<*имя_экземпляра*> — для [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]. Для веб-службы сервера отчетов по умолчанию используется виртуальный каталог **reportserver**. Для [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]используется виртуальный каталог по умолчанию **reports**.|  
  
 Ниже приведен пример полного URL-адреса.  
  
-   `http://+:80/reportserver`, предоставляет доступ к серверу отчетов.  
  
-   `http://+:80/reports`, предоставляет доступ к [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)].
  
##  <a name="bkmk_installwithwizard"></a> Установка в основном режиме с помощью мастера установки SQL Server  
 В следующем списке описываются конкретные шаги и параметры служб  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , выбираемые в мастере установки SQL Server. В этом списке описаны не все страницы мастера установки, а только страницы, связанные со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которые являются частью установки в собственном режиме.  
  
1.  Запустите мастер установки SQL Server (setup.exe) и выполните шаги, описанные на следующих страницах:  
  
    -   Ключ продукта  
  
    -   Условия лицензии  
  
    -   Глобальные правила  
  
    -   Центр обновления Майкрософт  
  
    -   Обновления продукта  
  
    -   Установка файлов установки  
  
    -   Установка правил  
  
2.  На странице **Роль установки** выберите **Установка компонентов SQL Server**.  
  
     ![Установка компонентов SQL Server для роли установки](../../reporting-services/install-windows/media/rs-setuprole.png "Установка компонентов SQL Server для роли установки")  
  
3.  Выберите следующие компоненты на странице **Выбор компонентов** :  
  
    -   (1) **Службы компонента Database Engine**, если еще не установлен компонент database engine.  
  
    -   (2) **Reporting Services-собственный режим**.  
  
     ![Выбор служб SSRS в собственном режиме в выборе компонентов](../../reporting-services/install-windows/media/rs-setupfeatureselection-native-withcircles.png "Выбор служб SSRS в собственном режиме в выборе компонентов")  
  
4.  Просмотрите переданные **правила компонентов** .  
  
5.  Учтите: если на странице "Конфигурация экземпляра" вы решили настроить **именованный экземпляр**, вам нужно будет использовать имя этого экземпляра в URL-адресах при переходе к диспетчеру отчетов и самому серверу отчетов. Если имя экземпляра — THESQLINSTANCE, URL-адреса будут выглядеть так:  
  
    -   `http://[ServerName]/ReportServer_THESQLINSTANCE`  
  
    -   `http://[ServerName]/Reports_THESQLINSTANCE`  
  
6.  **Конфигурация сервера**: если вы планируете использовать функцию подписки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , на странице **Конфигурация сервера** укажите **автоматический** тип запуска агента SQL Server.   Значение по умолчанию — вручную.  
  
7.  Добавьте администраторов SQL Server на странице **Конфигурация ядра СУБД** .  
  
8.  На странице **Конфигурация служб Reporting Services** выберите **Установка и настройка**.  
  
     ![Настройка служб SSRS в собственном режиме](../../reporting-services/install-windows/media/rs-setupconfiguration-native-with-circles.png "Настройка служб SSRS в собственном режиме")  
  
    > [!NOTE]  
    >  **Установка и настройка** будут доступны, только если для установки также выбрана функция базы данных.  
  
9. Правила конфигурации компонентов: проверьте переданные правила. Если все правила выполнены, мастер установки автоматически перейдет в состояние **готовности к установке** .  В контексте [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]эти правила позволяют проверить, существует ли каталог сервера отчетов и временный каталог базы данных.  
  
10. На странице **готовности к установке** запишите путь к файлу конфигурации — он понадобится вам позже для получения сводки о начальной конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая сведения об установленных компонентах, учетных записях служб и администраторах.  
  
11. После завершения мастера установки SQL Server проверьте установку собственного режима по умолчанию, используя следующие основные шаги.  
  
    -   Откройте диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и убедитесь, что вы можете подключиться к серверу отчетов.  
  
    -   Откройте браузер **с правами администратора** и подключитесь к диспетчеру отчетов служб [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)], например `http://localhost/Reports`.  
  
    -   Откройте браузер с правами администратора и подключитесь к странице сервера отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Например,  `http://localhost/ReportServer`  
  
 Дополнительные сведения см. в подразделе «Собственный режим» следующих двух разделов:  
  
 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)  
  
 [Устранение неполадок при установке служб Reporting Services](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
  
##  <a name="bkmk_additional_configuration"></a> Дополнительная настройка  
  
-   Инструкции по настройке интеграции [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)], позволяющей закреплять элементы отчета на панели мониторинга [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)], см. в статье [Интеграция сервера отчетов с Power BI](../../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
-   Инструкции по настройке электронной почты для обработки подписок см. в статьях [Настройки электронной почты — основной режим служб Reporting Services](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) и [Доставка электронной почтой в службах Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   Инструкции по настройке веб-портала для просмотра отчетов и управления ими с компьютера см. в статьях [Настройка брандмауэра для доступа к серверу отчетов](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md) и [Настройка сервера отчетов для удаленного администрирования](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md).  
  
## <a name="see-also"></a>См. также:

[Устранение неполадок при установке служб Reporting Services](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
[Проверка установки служб Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
[Настройка учетной записи службы сервера отчетов](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
[Настройка URL-адресов сервера отчетов](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
[Настройка подключения к базе данных сервера отчетов](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
[Установка в режиме "только файлы" (службы Reporting Services)](../../reporting-services/install-windows/files-only-installation-reporting-services.md)   
[Инициализация сервера отчетов](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
[Настройка соединений SSL для сервера отчетов, работающего в собственном режиме](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)   
[Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
