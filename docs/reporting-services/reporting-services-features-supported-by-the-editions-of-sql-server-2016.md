---
title: Возможности служб SQL Server Reporting Services, поддерживаемые различными выпусками
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.date: 06/20/2019
ms.openlocfilehash: 3e61381c2298a197be698ed82c247023ad708789
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893287"
---
# <a name="sql-server-reporting-services-features-supported-by-its-editions"></a>Возможности служб SQL Server Reporting Services, поддерживаемые различными выпусками

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

В этой статье описываются функции служб SQL Server Reporting Services (SSRS), поддерживаемые различными выпусками SQL Server. Выпуск SQL Server Evaluation доступен для ознакомления в течение 180 дней.  
  
 Заметки о последнем выпуске SQL Server см. в разделе [Заметки о выпуске SQL Server 2017](../sql-server/sql-server-2017-release-notes.md). Последние сведения о новых возможностях см. в статье [Новые возможности служб SQL Server Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).

 ## <a name="try-sql-server-2017"></a>Оцените SQL Server 2017

> [![Скачать SQL Server 2017](https://docs.microsoft.com/analysis-services/analysis-services/media/download.png)](https://go.microsoft.com/fwlink/?LinkID=829477) **[Скачать SQL Server 2017 на странице центра оценки](https://go.microsoft.com/fwlink/?LinkID=829477)**    
>
> ![Значок виртуальной машины Azure](https://docs.microsoft.com/analysis-services/analysis-services/media/azure-virtual-machine-small.png) **[Разверните виртуальную машину с уже установленным SQL Server 2017](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**    

Функции, поддерживаемые выпусками Evaluation и Developer, перечислены в столбце SQL Server Enterprise Edition в приведенной ниже таблице.

##  <a name="SSRS"></a> службы SQL Server Reporting Services  
  
|Имя функции|Enterprise|Standard|Web Edition|Express с дополнительными службами|Разработчик|  
|------------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Мобильные отчеты и аналитика|Да||||Да|  
|Поддерживаемый выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для базы данных каталога|Standard Edition или более многофункциональный|Standard Edition или более многофункциональный|Web Edition|Express|Standard Edition или более многофункциональный|  
|Поддерживаемый выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для источников данных|Все выпуски   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Все выпуски [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Web Edition|Express|Все выпуски [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|  
|Сервер отчетов|Да|Да|Да|Да|Да|  
|Конструктор отчетов|Да|Да|Да|Да|Да|  
|Веб-портал конструктора отчетов|Да|Да|Да|Да|Да|  
|Безопасность на основе ролей|Да|Да|Да|Да|Да|  
|Экспорт в Excel, PowerPoint, Word, PDF и графические форматы|Да|Да|Да|Да|Да|  
|Улучшенные датчики и диаграммы|Да|Да|Да|Да|Да|  
|Закрепление элементов отчета на панелях мониторинга [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]|Да|Да|Да|Да|Да|  
|Нестандартная проверка подлинности|Да|Да|Да||Да|  
|Отчет в виде веб-каналов данных|Да|Да|Да|Да|Да|  
|Поддержка моделей|Да|Да|Да||Да|  
|Создание пользовательских ролей в ролевой модели безопасности|Да|Да|||Да|  
|Безопасность элементов модели|Да|Да|||Да|  
|Бесконечный повтор дополнительной информации|Да|Да|||Да|  
|Библиотека общих компонентов|Да|Да|||Да|  
|Подписка и планирование по электронной почте и в общую папку|Да|Да|||Да|  
|Журнал отчета, моментальные снимки выполнения и кэширование|Да|Да|||Да|  
|Интеграция с SharePoint<sup>2</sup>|Да|Да|||Да|  
|Поддержка удаленных источников данных и источников данных, отличных от SQL<sup>1</sup>|Да|Да|||Да|  
|Источник данных, доставка, модуль подготовки отчетов, расширение RDCE|Да|Да|||Да|  
|Индивидуальная фирменная символика|Да||||Да|  
|Управляемая данными подписка на отчет|Да||||Да|  
|Масштабное развертывание (веб-фермы)|Да||||Да|  
|Предупреждения <sup>2</sup> (SSRS 2016) |Да||||Да|  
|Power View <sup>2</sup> (SSRS 2016) |Да||||Да| 
|Комментарии <sup>3</sup> |Да|Да|Да|Да|Да|  

 <sup>1</sup> Дополнительные сведения о поддерживаемых источниках данных в службах SQL Server Reporting Services (SSRS) см. в разделе [Источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
 <sup>2</sup> Требуется установка служб SQL Server 2016 Reporting Services в режиме интеграции с SharePoint. Дополнительные сведения см. в статье [Установка служб SQL Server Reporting Services в режиме интеграции с SharePoint](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md). Начиная с версии SQL Server 2017 Reporting Services интеграция с SharePoint больше не доступна. 

<sup>3</sup> Только в сервере отчетов Power BI и службах SQL Server 2017 Reporting Services или более поздней версии.

> [!NOTE]
> SQL Server Express с инструментами и SQL Server Express не поддерживают службы SQL Server Reporting Services.
  
## <a name="edition-requirements-for-the-report-server-database"></a>Требования к выпуску для базы данных сервера отчетов
 При создании базы данных сервера отчетов не все выпуски SQL Server [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно использовать для ее размещения. В таблице ниже перечислены выпуски компонента [!INCLUDE[ssDE](../includes/ssde-md.md)], которые пригодны для конкретных выпусков служб SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Для данного выпуска служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Используйте данный выпуск экземпляра компонента Database Engine для размещения базы данных|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Выпуски Enterprise или Standard (локальные или удаленные)|  
|Standard|Выпуски Enterprise или Standard (локальные или удаленные)|  
|Web Edition|Выпуск Web edition (только локально)|  
|Express с дополнительными службами|Express с дополнительными службами (только локальная версия)|  
|Ознакомительная версия|Ознакомительная версия|  
  
##  <a name="BIC"></a> Клиенты бизнес-аналитики  
Перечисленные ниже клиентские приложения доступны в центре загрузки Майкрософт. Они помогают создавать документы бизнес-аналитики, запускаемые в экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При размещении этих документов в серверной среде используйте выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , поддерживающий этот тип документов. В следующей таблице показано, какой выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] содержит компоненты сервера, необходимые для размещения документов, созданных в этих клиентских приложениях.  
  
|Имя средства|Enterprise|Standard|Web Edition|Express с дополнительными службами|Разработчик|  
|---------------|----------------|--------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)], **.rdl** и **.rds**|Да|Да|Да|Да|Да|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)], **.rsmobile**|Да||||Да|  
|Приложения Power BI для мобильных устройств (iOS, Windows 10 и Android), **.rsmobile**|Да||||Да|  
  
> [!NOTE]  
> * В таблице выше указаны выпуски [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], необходимые для включения этих клиентских средств. Однако эти средства могут обращаться к данным, размещенным в любом выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
> * [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] является единственной точкой для создания мобильных отчетов. Подключитесь к серверу SSRS, чтобы получить доступ к источникам данных и создать отчеты. Затем опубликуйте их на сервере SSRS, чтобы другие пользователи организации могли работать с ними (на сервере или мобильных устройствах). Можно также использовать [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] автономно с локальными источниками данных.  
> * Независимо от того, используете ли вы [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] локально, [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] в облаке или оба решения в качестве системы доставки отчетов, для доступа к панелям мониторинга и мобильным отчетам на мобильных устройствах требуется только одно мобильное приложение. Приложения [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] доступны для загрузки из магазинов приложений Windows, iOS или Android.  

## <a name="next-steps"></a>Следующие шаги

* Ознакомьтесь с [возможностями, поддерживаемыми различными выпусками SQL Server 2017](~/sql-server/editions-and-components-of-sql-server-2017.md). 

* [Спланируйте установку SQL Server](../sql-server/install/planning-a-sql-server-installation.md).

* Остались вопросы? Задайте их на [форуме служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
