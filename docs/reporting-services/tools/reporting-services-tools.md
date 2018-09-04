---
title: Средства служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 05/31/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SSRS, tools
- Reporting Services, tools
- components [Reporting Services]
- components [Reporting Services], about components
- Reporting Services, components
- SSRS, components
- reports [Reporting Services], tools
- SQL Server Reporting Services, components
- SQL Server Reporting Services, tools
- architecture [Reporting Services]
ms.assetid: 23d616e3-eb90-43fb-9b7a-869bd7e22e7b
caps.latest.revision: 80
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d28fa938f672d008949c745aec10db9a3b5d93ff
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2018
ms.locfileid: "40410484"
---
# <a name="reporting-services-tools"></a>Инструментальные средства служб Reporting Services
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] содержат набор графических средств и средств для работы со скриптами, поддерживающих разработку и использование отчетов с широкими возможностями в управляемой среде. В набор средств входят средства разработки, настройки и администрирования, а также средства просмотра отчетов. В этом разделе содержится краткий обзор средств в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и способов доступа к ним.  
  
 Сведения о том, как быстро найти нужное средство, см. в разделе [Учебник. Инструкции по поиску и запуску средств служб Reporting Services (SSRS)](../../reporting-services/tools/tutorial-how-to-locate-and-start-reporting-services-tools-ssrs.md).  
  
## <a name="tools-for-report-authoring"></a>Средства разработки отчетов  
 В следующей таблице перечислены доступные средства для создания отчетов в службах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
|Инструмент|Описание|Способ доступа|  
|----------|-----------------|-------------------|  
|[!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]|С помощью [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)]можно создавать мобильные отчеты, которые динамически настраивают содержимое по размеру экрана или окна браузера и хорошо масштабируются под любой размер экрана.<br /><br /> Мобильные отчеты можно создавать в области конструктора с настраиваемыми строками и столбцами сетки, а также гибкими элементами мобильных отчетов.<br /><br /> Дополнительные сведения см. в разделе [Создание мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md).|Загрузите [издатель мобильных отчетов SQL Server](http://go.microsoft.com/fwlink/?LinkId=733527)|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]|интерактивное средство для просмотра и визуализации данных, предназначенное для создания отчетов на основе табличных моделей служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и взаимодействия с ними.|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. Браузер с приложением Silverlight.|  
|конструктор отчетов|Это средство служит для разработки отчетов. В него входят следующие функции.<br /><br /> Развертывание на сервере отчетов в режиме интеграции с SharePoint или в основном режиме.<br /><br /> Располагается в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<br /><br /> Область данных отчета для упорядочивания данных в отчете<br /><br /> Представления с вкладками для проектирования и предварительного просмотра для интерактивного конструирования отчета<br /><br /> Конструкторы запросов позволяют указывать, какие данные извлекать из источников данных и какие данные связаны с типами источников данных в [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)<br /><br /> Редактор выражений с поддержкой технологии IntelliSense для создания выражений [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , позволяющих настраивать содержимое и внешний вид отчетов<br /><br /> Поддерживает пользовательские элементы отчетов и пользовательские конструкторы запросов<br /><br /> <br /><br /> Дополнительные сведения см. в разделе [Службы Reporting Services в SQL Server Data Tools (службы SSDT)](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md).|[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|  
|построитель отчетов|Это средство служит для разработки отчетов. В него входят следующие функции.<br /><br /> Развертывание на сервере отчетов в режиме интеграции с SharePoint или в основном режиме.<br /><br /> Среда создания отчетов, сходная с [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office[!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]<br /><br /> Возможность сохранять элементы отчетов как части отчета<br /><br /> Мастер создания карт<br /><br /> Агрегаты агрегатов<br /><br /> Улучшенная поддержка выражений<br /><br /> Конструкторы запросов позволяют указывать, какие данные извлекать из выбранных встроенных типов источников данных<br /><br /> Дополнительные сведения см. в разделе [Построитель отчетов в SQL Server 2016](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md).|Скачайте [автономную версию построителя отчетов](http://go.microsoft.com/fwlink/?LinkID=219138)<br /><br /> Либо откройте его из диспетчера отчетов или SharePoint.|  
  
## <a name="tools-for-report-server-administration"></a>Средства для администрирования сервера отчетов  
 В службах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]доступен набор графических средств и средств работы со скриптами для администрирования сервера отчетов. Используемые средства зависят от режима развертывания сервера отчетов.  
  
### <a name="native-mode"></a>Собственный режим  
 В следующей таблице приведены доступные средства администрирования сервера отчетов, развернутого в собственном режиме.  
  
|Инструмент|Описание|Способ доступа|  
|----------|-----------------|-------------------|  
|Диспетчер конфигурации служб Reporting Services|Это средство используется для настройки установки служб Reporting Services. Доступны следующие задачи.<br /><br /> Настройка локальных и удаленных экземпляров сервера отчетов<br /><br /> Настройка учетной записи службы сервера отчетов.<br /><br /> Создание и настройка одного или нескольких URL-адресов веб-службы.<br /><br /> Настройка URL-адреса диспетчера отчетов<br /><br /> Создание и настройка базы данных сервера отчетов.<br /><br /> Настройка масштабного развертывания.<br /><br /> Резервное копирование, восстановление или замена симметричного ключа, используемого для шифрования хранимых строк подключения и учетных данных.<br /><br /> Настройка учетной записи автоматического выполнения.<br /><br /> Настройка SMTP-сервера для доставки электронной почты.<br /><br /> <br /><br /> Примечание. Диспетчер настройки служб Reporting Services не предназначен для управления содержимым сервера отчетов, включения дополнительных компонентов или предоставления доступа к серверу.<br /><br /> Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).|Меню «Пуск»|  
|SQL Server Management Studio|Это средство используется для управления одним или несколькими экземплярами сервера отчетов в единой среде, включая следующие действия.<br /><br /> Управление локальными и удаленными экземплярами сервера отчетов<br /><br /> Установка свойств сервера отчетов<br /><br /> Изменение определений ролей<br /><br /> Отключение неиспользуемых функций сервера отчетов.<br /><br /> Управление заданиями<br /><br /> Управление общими расписаниями|Меню «Пуск»|  
|Диспетчер конфигурации SQL Server|Это средство используется для следующих целей.<br /><br /> Запуск и остановка служб Windows Reporting Services<br /><br /> Настройка передачи отзывов пользователей, расположения каталога дампа и отчетов об ошибках<br /><br /> <br /><br /> **\*\* Предупреждение. \*\*** Не используйте это средство для настройки учетных записей службы. Используйте вместо него средство настройки служб Reporting Services.<br /><br /> Дополнительные сведения см. в разделе [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md).|Меню «Пуск»|  
|Программа rsconfig|Это средство используется для настройки соединения сервера отчетов с базой данных сервера отчетов и управления им. Кроме того, с ее помощью можно указать учетную запись пользователя, которую следует использовать для автоматической обработки отчетов.<br /><br /> Дополнительные сведения см. в разделе [Программы командной строки сервера отчетов (службы SSRS)](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md).|С помощью командной строки|  
|Программа rskeymgmt|Это средство используется для следующих целей.<br /><br /> Извлечение, восстановление, создание и удаление симметричного ключа, используемого для шифрования данных сервера отчетов<br /><br /> Соединение экземпляров сервера отчетов при масштабном развертывании<br /><br /> <br /><br /> Дополнительные сведения см. в разделе [Программы командной строки сервера отчетов (службы SSRS)](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md).|С помощью командной строки|  
|Классы инструментария управления Windows (WMI)|Эти классы используются для автоматизации задач настройки в диспетчере конфигурации служб Reporting Services без использования графического пользовательского интерфейса.<br /><br /> Дополнительные сведения см. в разделе [Accessing the WMI Provider Programmatically](../../reporting-services/accessing-the-wmi-provider-programmatically.md).|Скрипт Visual Basic|  
  
### <a name="sharepoint-integrated-mode"></a>Режим интеграции с SharePoint  
 В режиме SharePoint службы Reporting Services являются приложением-службой в архитектуре SharePoint и администрируются непосредственно через SharePoint  
  
|Инструмент|Описание|Способ доступа|  
|----------|-----------------|-------------------|  
|Центр администрирования SharePoint|Центр администрирования SharePoint используется для создания, запросов и управления общими приложениями-службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> Дополнительные сведения см. в разделе [Настройка и администрирование сервера отчетов (режим интеграции с SharePoint служб Reporting Services)](../../reporting-services/report-server-sharepoint/configuration-and-administration-of-a-report-server.md).|Открытие центра администрирования в браузере по URL-адресу сайта SharePoint|  
|Командлеты PowerShell|Командлеты PowerShell используются для создания, запросов и управления общими приложениями-службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> Дополнительные сведения см. в разделе [Командлеты PowerShell для служб Reporting Services в режиме интеграции с SharePoint](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).|Консоль управления SharePoint 2010|  
  
## <a name="tools-for-report-content-management"></a>Средства управления содержимым отчетов  
 В службах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]доступен набор графических средств и средств работы со скриптами для управления содержимым. Используемые средства зависят от режима развертывания сервера отчетов.  
  
|Инструмент|Описание|Способ доступа|  
|----------|-----------------|-------------------|  
|URL-адрес веб-службы сервера отчетов|Это средство используется для просмотра содержимого каталога отчетов на общей странице навигации по элементам.<br /><br /> Дополнительные сведения см. в разделе [Report Server Web Service](../../reporting-services/report-server-web-service/report-server-web-service.md).|Браузер|  
|Веб-портал|**(Только в собственном режиме)** Это средство предназначено для администрирования одного экземпляра удаленного сервера отчетов через HTTP-соединение. Можно сделать следующее.<br /><br /> Просмотр, поиск, печать отчетов и подписка на отчеты.<br /><br /> Создания, защиты и поддержания иерархии папок для организации элементов на сервере.<br /><br /> Настройки безопасности на основе ролей, определяющей доступ к элементам и операциям.<br /><br /> Настройки свойств выполнения отчета, истории отчета и параметров отчета.<br /><br /> Создание моделей отчета, которые подключаются и получают данные из источника данных служб Microsoft SQL Server Analysis Services из реляционного источника данных SQL Server.<br /><br /> Задайте параметры безопасности элементов модели, чтобы обеспечить доступ к конкретным сущностям в модели, или сопоставьте сущности со стандартными отчетами с дополнительной информацией, созданными заранее.<br /><br /> Создания общего расписания и общих источников данных, чтобы упростить управление расписанием и соединениями с источниками данных.<br /><br /> Создания подписок, управляемых данными, которые распространяют отчеты среди большого количества получателей.<br /><br /> Создания связанных отчетов для повторного использования существующих отчетов различными способами.<br /><br /> Запустите построитель отчетов для создания отчетов, которые можно сохранить и запустить на сервере отчетов. Дополнительные сведения см. в статье [Web portal (SSRS Native Mode)](../../reporting-services/web-portal-ssrs-native-mode.md).| Браузер  
|Программа rs|Это средство является сервером скриптов, используемым для выполнения операций в форме скриптов. Используйте эту программу для выполнения скриптов [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , предназначенных для копирования данных из одной базы данных сервера отчетов в другую, публикации отчетов, создания объектов в базе данных сервера отчетов и т. д. Дополнительные сведения см. в разделе [Программы командной строки сервера отчетов (службы SSRS)](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md).|С помощью командной строки|  
  
## <a name="see-also"></a>См. также:  
 [Сервер отчетов служб Reporting Services](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)   
 [Основные понятия служб Reporting Services (SSRS)](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [Службы Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
