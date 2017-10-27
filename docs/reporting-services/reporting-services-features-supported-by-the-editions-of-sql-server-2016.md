---
title: "Функции, поддерживаемые различными выпусками SQL Server 2016 служб Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 39f03d2d-6e48-4b34-a9d3-07f86313b937
caps.latest.revision: 3
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ac4f1eeab19ac0a7468c62ac3fa8dfcc33b12f45
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---

# <a name="reporting-services-features-supported-by-the-editions-of-sql-server-2016"></a>Возможности служб Reporting Services, поддерживаемые различными выпусками SQL Server 2016

В этом разделе подробно описаны функции, поддерживаемые различными выпусками SQL Server 2016.  
  
 Выпуск SQL Server Evaluation доступен для ознакомления в течение 180 дней.  
  
 Заметки о последнем выпуске см. в разделе [Заметки о выпуске SQL Server 2016](../sql-server/sql-server-2016-release-notes.md). Последние сведения о новых возможностях см. в разделе [Новые возможности служб Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).
    
 **Оцените SQL Server 2016!**    
    
 > [![Скачать на странице центра оценки](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Скачайте SQL Server 2016 на странице центра оценки](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Значок виртуальной машины Azure](../analysis-services/media/azure-virtual-machine-small.png) **[Разверните виртуальную машину с уже установленным SQL Server 2016](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    

Компоненты, поддерживаемые выпусками Evaluation и Developer, перечислены в разделе SQL Server Enterprise Edition.

Чтобы перейти к таблице, относящейся к технологии SQL Server, щелкните ссылку на нее:  

-   [Службы Reporting Services](#SSRS)  
  
-   [Клиенты бизнес-аналитики](#BIC)  

##  <a name="SSRS"></a> Службы Reporting Services  
  
|Имя функции|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express с инструментами|Express|Разработчик|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Мобильные отчеты и ключевые показатели эффективности|Да||||||Да|  
|Поддерживаемый выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для базы данных каталога|Standard Edition или более многофункциональный|Standard Edition или более многофункциональный|Web Edition|Express|||Standard Edition или более многофункциональный|  
|Поддерживаемый выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для источников данных|Все выпуски   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Все выпуски [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Web Edition|Express|||Все выпуски [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|  
|Сервер отчетов|Да|Да|Да|Да|||Да|  
|Конструктор отчетов|Да|Да|Да|Да|||Да|  
|Веб-портал конструктора отчетов|Да|Да|Да|Да|||Да|  
|Ролевая модель безопасности|Да|Да|Да|Да|||Да|  
|Экспорт в Excel, PowerPoint, Word, PDF и графические форматы|Да|Да|Да|Да|||Да|  
|Улучшенные датчики и диаграммы|Да|Да|Да|Да|||Да|  
|Закрепление элементов отчета на панелях мониторинга [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]|Да|Да|Да|Да|||Да|  
|Нестандартная проверка подлинности|Да|Да|Да|Да|||Да|  
|Отчет в виде веб-каналов данных|Да|Да|Да|Да|||Да|  
|Поддержка моделей|Да|Да|Да||||Да|  
|Создание пользовательских ролей в ролевой модели безопасности|Да|Да|||||Да|  
|Безопасность элементов модели|Да|Да|||||Да|  
|Бесконечный повтор дополнительной информации|Да|Да|||||Да|  
|Библиотека общих компонентов|Да|Да|||||Да|  
|Подписка и планирование по электронной почте и в общую папку|Да|Да|||||Да|  
|Журнал отчета, моментальные снимки выполнения и кэширование|Да|Да|||||Да|  
|Интеграция с SharePoint|Да|Да|||||Да|  
|Поддержка удаленных источников данных и источников данных, отличных от SQL<sup>1</sup>|Да|Да|||||Да|  
|Источник данных, доставка и модуль подготовки отчетов, расширение RDCE|Да|Да|||||Да|  
|Индивидуальная фирменная символика|Да||||||Да|  
|Управляемые данными подписки на отчет|Да||||||Да|  
|Масштабное развертывание (веб-фермы)|Да||||||Да|  
|Предупреждения<sup>2</sup>|Да||||||Да|  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] <sup>2</sup>|Да||||||Да|  
  
 <sup>1</sup> Дополнительные сведения о поддерживаемых источниках данных в SQL Server 2016 Reporting Services (SSRS) см. в разделе [источники данных, поддерживаемые службой Reporting Services &#40; Службы SSRS &#41; ](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
 <sup>2</sup> требуется установка служб Reporting Services в режиме SharePoint. Дополнительные сведения см. в разделе [Установка служб Reporting Services в режиме SharePoint](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
## <a name="report-server-database-server-edition-requirements"></a>Требования к выпуску серверной базы данных сервера отчетов  
 При создании базы данных сервера отчетов помните, что не все выпуски [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно использовать для ее хранения. В следующей таблице перечислены выпуски компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , которые пригодны для конкретных выпусков служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Для данного выпуска службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Используйте данный выпуск экземпляра компонента Database Engine для хранения базы данных|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Выпуски Enterprise или Standard (локальные или удаленные)|  
|Standard Edition|Выпуски Enterprise или Standard (локальные или удаленные)|  
|Web Edition|Выпуск Web edition (только локально)|  
|Express с дополнительными службами|Express с дополнительными службами (только локальная версия).|  
|Ознакомительная версия|Ознакомительная версия|  
  
##  <a name="BIC"></a> Клиенты бизнес-аналитики  
 Следующие клиентские приложения доступны в центре загрузки Майкрософт и предоставляются с целью упростить создание документов бизнес-аналитики, запускаемых в экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . При размещении этих документов в серверной среде используйте выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , поддерживающий этот тип документов. В следующей таблице показано, какой выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] содержит компоненты сервера, необходимые для размещения документов, созданных в этих клиентских приложениях.  
  
|Имя средства|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express с инструментами|Express|Разработчик|  
|---------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] (.rdl и .rds)|Да|Да|||||Да|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] (.rsmobile)|Да||||||Да|  
|Приложения Power BI для мобильных устройств (iOS, Windows 10, Android) (.rsmobile)|Да||||||Да|  
  
> [!NOTE]  
> 1.  В таблице выше указаны выпуски [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , необходимые для включения этих клиентских средств, но сами инструменты могут обращаться к данным, размещенным в любом выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
> 2.  [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] является единственной точкой для создания мобильных отчетов. Подключитесь к серверу [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , чтобы получить доступ к источникам данных и создать отчеты. Затем публикуйте их на сервере [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , чтобы другие пользователи организации могли работать с ними (на сервере или мобильных устройствах). Можно также использовать [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] автономно с локальными источниками данных  
> 3.  Независимо от того, используете ли  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] локально, [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] в облаке или оба решения в качестве системы доставки отчетов, для доступа к панелям мониторинга и мобильным отчетам на мобильных устройствах требуется только одно мобильное приложение. Приложения [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] доступны для загрузки из магазинов приложений Windows, iOS или Android.  

## <a name="next-steps"></a>Следующие шаги

[Возможности, поддерживаемые различными выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)  
[Спецификации SQL Server 2016](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)  
[Установка SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md) 

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

