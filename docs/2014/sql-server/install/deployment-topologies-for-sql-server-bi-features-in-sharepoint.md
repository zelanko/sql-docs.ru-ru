---
title: Топологии развертывания для компонентов бизнес-Аналитики SQL Server в SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 39f76bc7-94e6-4dbc-bfa5-d56f4430bb26
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7ef3ecf31c0539f3b3cb2cf5a4f04b044e625bd1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095596"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>Deployment Topologies for SQL Server BI Features in SharePoint
  В этом разделе описываются типовые топологии для установки компонентов SQL Server Business Intelligence [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] в средах SharePoint 2010 и SharePoint 2013. Например, один сервер и три уровня.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 #124; SharePoint 2010|  
  
 **В этом разделе:**  
  
-   [SharePoint 2013 образцовые топологии развертывания](#bkmk_example_deployments_2013)  
  
    -   [Развертывание трех серверов служб PowerPivot для SharePoint 2013 и создания отчетов](#bkmk_bi_Sharepoint2013_3tier)  
  
    -   [Развертывание PowerPivot для SharePoint 2013 одного сервера](#bkmk_powerpivot_sharepoint2013_1server)  
  
    -   [Развертывание PowerPivot для SharePoint 2013 два сервера](#bkmk_powerpivot_sharepoint2013_2server)  
  
    -   [Развертывание PowerPivot для SharePoint 2013 три сервера](#bkmk_powerpivot_sharepoint2013_3server)  
  
    -   [PowerPivot для SharePoint 2013 и служб Reporting Services развертывание с одним сервером](#bkmk_powerpivot_ssrs_sharepoint2013_1server)  
  
    -   [Развертывание двух серверов служб PowerPivot для SharePoint 2013 и создания отчетов](#bkmk_powerpivot_ssrs_sharepoint2013_2server)  
  
-   [SharePoint 2010 образцовые топологии развертывания](#bkmk_example_deployments_2010)  
  
    -   [Развертывание одного сервера](#bkmk_sharepoint2010_1server)  
  
    -   [Двухуровневое развертывание](#bkmk_sharepoint2010_2server)  
  
    -   [3 уровневого развертывания](#bkmk_sharepoint2010_3server)  
  
    -   [Трехуровневой конфигурации с масштабным развертыванием](#bkmk_sharepoint2010_scaleserver)  
  
##  <a name="bkmk_example_deployments_2013"></a> SharePoint 2013 образцовые топологии развертывания  
 Режим установки SQL Server **PowerPivot для SharePoint** не зависит от SharePoint. Он не использует объектную модель или интерфейсы SharePoint для поддержки интеграции. Поэтому службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно установить только на компьютере, работающем под управлением Windows Server 2008 R2 или более поздней версии. Это может быть (но необязательно) сервер приложений в ферме SharePoint. Один из шагов настройки — связать службы Excel с сервером, работающим с [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Для балансировки нагрузки и отказоустойчивости рекомендуется установить и зарегистрировать несколько серверов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , работающих в режиме интеграции с SharePoint.  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Для работы в режиме интеграции с SharePoint** необходим сервер SharePoint 2013 и архитектура приложения службы SharePoint.  
  
 В следующих разделах приведены типичные топологии развертывания:  
  
###  <a name="bkmk_bi_Sharepoint2013_3tier"></a> Развертывание трех серверов служб PowerPivot для SharePoint 2013 и создания отчетов  
 В следующем трехсерверном развертывании компонент SQL Server Database Engine, сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint, а также SharePoint выполняются на отдельных серверах. Пакет установщика [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013 PowerPivot (**spPowerPivot.msi**) должен запускаться на сервере SharePoint.  
  
 ![Режим интеграции служб SSAS и SSRS с SharePoint 3 развертывания сервера](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "SSAS и SSRS с SharePoint 3 режим развертывания сервера")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(4)**|Установите надстройку служб Reporting Services для SharePoint с установочного носителя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**(5)**|Запустите **spPowerPivot.msi** для установки поставщиков данных, средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и указания времени обновления данных.|  
|**(6)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**(7)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
 ![Параметры SharePoint](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "параметры SharePoint") [отправить отзыв и контактные данные через Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
###  <a name="bkmk_powerpivot_sharepoint2013_1server"></a> Развертывание PowerPivot для SharePoint 2013 одного сервера  
 Развертывание одиночного сервера полезно для тестирования, но не рекомендуется для производственных целей.  
  
 На следующей диаграмме показаны компоненты, которые входят в состав развертывания [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] одиночного сервера.  
  
 ![PowerPivot для развертывания сервера SharePoint одним](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "PowerPivot для SharePoint одного сервера развертывания")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
|**(4)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_2server"></a> Развертывание PowerPivot для SharePoint 2013 два сервера  
 В следующем развертывании двух серверов компонент SQL Server Database Engine и службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint выполняются на сервере, где нет SharePoint. Для SharePoint 2013 пакет установщика [!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)] (**spPowerPivot.msi**) устанавливается на сервере SharePoint.  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] расширяет возможности SharePoint Server 2013 для добавления данных на сервере обработки и обновления, поставщики данных, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] коллекции, а также поддержку управления [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книги и книги Excel с расширенными моделями данных.  
  
 Пакет установщика доступен в составе пакета дополнительных компонентов [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Пакет дополнительных компонентов можно загрузить из [!INCLUDE[msCoName](../../includes/msconame-md.md)] центра загрузки Майкрософт по [PowerPivot® Microsoft® SQL Server® 2014 для Microsoft® SharePoint®](https://go.microsoft.com/fwlink/?LinkID=296473) (HYPERLINK "<https://go.microsoft.com/fwlink/?LinkID=296473>" \t «_blank» <https://go.microsoft.com/fwlink/?LinkID=296473>).  
  
 ![Развертывание сервера в режиме PowerPivot 2 SSAS](../../../2014/analysis-services/media/as-powerpivot-mode-2server-deployment.gif "развертывание сервера в режиме PowerPivot 2 SSAS")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|ЗАПУСТИТЕ **spPowerPivot.msi** для установки поставщиков данных, средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и указания времени обновления данных.|  
|**(4)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**(5)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_3server"></a> Развертывание PowerPivot для SharePoint 2013 три сервера  
 В следующем трехсерверном развертывании компонент SQL Server Database Engine, сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint, а также SharePoint выполняются на отдельных серверах. Пакет установщика [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 (spPowerPivot.msi) должен быть установлен на сервере SharePoint.  
  
 ![КАК развертывание сервера в режиме AS PowerPivot 3](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "как развертывание сервера в режиме AS PowerPivot 3")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|ЗАПУСТИТЕ spPowerPivot.msi для установки поставщиков данных, средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и указания времени обновления данных.|  
|**(4)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**(5)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a> PowerPivot для SharePoint 2013 и служб Reporting Services развертывание с одним сервером  
 Развертывание одиночного сервера полезно для тестирования, но не рекомендуется для производственных целей.  
  
 ![Режим интеграции служб SSAS и SSRS с SharePoint 1 развертывания сервера](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "SSAS и SSRS с SharePoint режим 1 развертывания сервера")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|Приложение службы PowerPivot. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(4)**|Установите надстройку служб Reporting Services для SharePoint с установочного носителя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**(5)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
|**(6)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a> Развертывание двух серверов служб PowerPivot для SharePoint 2013 и создания отчетов  
 В следующем двухсерверном развертывании ядро СУБД SQL Server и сервер Analysis Services в режиме интеграции с SharePoint работают на сервере, отдельном от SharePoint. PowerPivot для SharePoint 2013 пакет установщика **(spPowerPivot.msi)** должна выполняться на сервере SharePoint.  
  
 ![SSAS и развертывание сервера в режиме интеграции с SharePoint 2 служб SSRS](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "SSAS и развертывание сервера в режиме интеграции с SharePoint 2 служб SSRS")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|Приложение службы PowerPivot. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(4)**|Установите надстройку служб Reporting Services для SharePoint с установочного носителя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**(5)**|ЗАПУСТИТЕ файл **spPowerPivot.msi** для установки поставщиков данных, средства настройки PowerPivot, коллекции PowerPivot и обновления данных по расписанию.|  
|**(6)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**(7)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
##  <a name="bkmk_example_deployments_2010"></a> SharePoint 2010 образцовые топологии развертывания  
 На следующей диаграмме показано, какие службы и поставщики работают на каждом из уровней. Обратите внимание, что диаграмма включает несколько встроенных служб. Эти службы необходимы для поддержки некоторых сценариев SQL Server BI. Службы Excel Services, Secure Store и Claims to Windows Token Service либо необходимы, либо рекомендуются для поддержки работы PowerPivot для SharePoint или служб Reporting Services в SharePoint. Кроме того, для поддержки некоторых сценариев доступа к данным PowerPivot необходимы поставщики MSOLAP OLE DB и службы ADO.NET. Дополнительно можно установить на уровне данных службу Analysis Services, если предполагается создавать отчеты [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] на основе баз данных табличных моделей, размещенных за пределами SharePoint.  
  
 ![Диаграмма логической архитектуры](../../../2014/sql-server/install/media/sql11bisetup.gif "диаграмма логической архитектуры")  
  
##  <a name="bkmk_sharepoint2010_1server"></a> Развертывание одного сервера  
 Все компоненты сервера, включая уровень данных, можно установить на одном компьютере. Такая конфигурация развертывания полезна при ознакомлении с ПО или при разработке пользовательских приложений, включающих службы Reporting Services в режиме SharePoint. Это развертывание является наиболее простым в настройке. Поскольку все компоненты устанавливаются на одном и том же компьютере, требуется также наименьшее количество лицензий. Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] и компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] устанавливаются как однолицензионная копия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Чтобы установить все компоненты на одиночный сервер, последовательно установите службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] на один и тот же физический сервер. Инструкции по настройке отдельного сервера, см. в разделе [контрольный список развертывания: Службы Reporting Services, Power View и PowerPivot для SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).  
  
##  <a name="bkmk_sharepoint2010_2server"></a> Двухуровневое развертывание  
 Двухуровневое развертывание обычно включает установку SharePoint Server 2010 на один компьютер и компонент SQL Server Database Engine на второй компьютер. Перемещение уровня данных на выделенный сервер — это наиболее типичная конфигурация двухкомпьютерной фермы. В двухуровневой ферме на сервере SharePoint устанавливаются служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и служба [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Все веб-службы на сервере, обслуживающем клиентские запросы, и общие службы на уровне приложений эксплуатируются на одном и том же физическом сервере. Шаги по установке в двухуровневой конфигурации очень похожи на установку на отдельном сервере: службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] последовательно устанавливаются на одном и том же физическом сервере.  
  
##  <a name="bkmk_sharepoint2010_3server"></a> 3 уровневого развертывания  
 В трехуровневом развертывании обычно отделяют службы клиентского веб-интерфейса от приложений, интенсивно использующих память. В этой топологии службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] устанавливаются только на сервере приложений. Веб-службы, выполняющиеся на клиентском веб-интерфейсе, устанавливаются как решения, которые развернуты в качестве приложений в ферме в процессе настройки сервера, как задача после установки. На следующей диаграмме проиллюстрировано трехуровневое развертывание.  
  
 ![Топология из 3 серверов](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "топология из трех серверов")  
  
##  <a name="bkmk_sharepoint2010_scaleserver"></a> Трехуровневой конфигурации с масштабным развертыванием  
 Эта топология иллюстрирует масштабное развертывание, при котором одна и та же общая служба выполняется на нескольких серверах, что позволяет обслуживать большое количество запросов и предоставлять дополнительные мощности по обработке данных PowerPivot или отчетов служб Reporting Services. На нижеследующей диаграмме показаны три кластера серверов приложений, в каждом из которых в различных сочетаниях выполняются общие службы. В среде SharePoint функции обнаружения и проверки доступности служб встроены в ферму. Балансировка загрузки нескольких физических серверов, на которых выполняется одно и то же приложение общей службы, является частью архитектуры общих служб.  
  
 При развертывании многосерверной фермы, обязательно следуйте инструкциям в статье по SharePoint: [Несколько серверов для трехуровневой фермы (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834).  
  
 ![Топология из пяти серверов](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "топология из пяти серверов")  
  
## <a name="see-also"></a>См. также  
 [Установку в режиме интеграции с SharePoint служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Установка PowerPivot для SharePoint 2013](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)   
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
