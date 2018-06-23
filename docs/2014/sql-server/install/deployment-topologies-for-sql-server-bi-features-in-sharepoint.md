---
title: Топологии развертывания для компонентов бизнес-Аналитики SQL Server в SharePoint | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39f76bc7-94e6-4dbc-bfa5-d56f4430bb26
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: b8c0dbc85806d0b092cf1de7bbe839b218d59164
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191145"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>Deployment Topologies for SQL Server BI Features in SharePoint
  В этом разделе описываются типовые топологии для установки компонентов SQL Server Business Intelligence [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] в средах SharePoint 2010 и SharePoint 2013. Например, один сервер и три уровня.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 #124; SharePoint 2010|  
  
 **В этом разделе:**  
  
-   [Примеры топологии развертывания SharePoint 2013](#bkmk_example_deployments_2013)  
  
    -   [Развертывание трех серверов служб PowerPivot для SharePoint 2013 и создания отчетов](#bkmk_bi_Sharepoint2013_3tier)  
  
    -   [Развертывание PowerPivot для SharePoint 2013 одного сервера](#bkmk_powerpivot_sharepoint2013_1server)  
  
    -   [Развертывание PowerPivot для SharePoint 2013 два сервера](#bkmk_powerpivot_sharepoint2013_2server)  
  
    -   [Развертывание PowerPivot для SharePoint 2013 три сервера](#bkmk_powerpivot_sharepoint2013_3server)  
  
    -   [PowerPivot для развертывания на одном сервере SharePoint 2013 и служб Reporting Services](#bkmk_powerpivot_ssrs_sharepoint2013_1server)  
  
    -   [PowerPivot для SharePoint 2013 и службы Reporting Services развертывание двух серверов](#bkmk_powerpivot_ssrs_sharepoint2013_2server)  
  
-   [Образцовые топологии развертывания SharePoint 2010](#bkmk_example_deployments_2010)  
  
    -   [Развертывание одного сервера](#bkmk_sharepoint2010_1server)  
  
    -   [Двухуровневое развертывание](#bkmk_sharepoint2010_2server)  
  
    -   [Трехуровневое развертывание](#bkmk_sharepoint2010_3server)  
  
    -   [Трехуровневое масштабное развертывание](#bkmk_sharepoint2010_scaleserver)  
  
##  <a name="bkmk_example_deployments_2013"></a> Примеры топологии развертывания SharePoint 2013  
 Режим установки SQL Server **PowerPivot для SharePoint** не зависит от SharePoint. Он не использует объектную модель или интерфейсы SharePoint для поддержки интеграции. Таким образом [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно установить на любом компьютере под управлением Windows Server 2008 R2 или более поздней версии. Это может быть (но необязательно) сервер приложений в ферме SharePoint. Один из шагов настройки — связать службы Excel с сервером, работающим с [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Для балансировки нагрузки и отказоустойчивости рекомендуется установить и зарегистрировать несколько серверов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], работающих в режиме интеграции с SharePoint.  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режиме интеграции с SharePoint** необходим сервер SharePoint 2013 и архитектура приложения службы SharePoint.  
  
 В следующих разделах приведены типичные топологии развертывания:  
  
###  <a name="bkmk_bi_Sharepoint2013_3tier"></a> Развертывание трех серверов служб PowerPivot для SharePoint 2013 и создания отчетов  
 В следующем развертывании трех серверов SQL Server Database Engine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] сервера, работающего в режиме интеграции с SharePoint и SharePoint, каждое выполнение на отдельном сервере. [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013 пакет установщика (**spPowerPivot.msi**) должна выполняться на сервере SharePoint.  
  
 ![Режим интеграции служб SSAS и SSRS с SharePoint 3 развертывания сервера](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "SSAS и SSRS с SharePoint 3 режим развертывания сервера")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|Приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|**(4)**|Установите надстройку служб Reporting Services для SharePoint с установочного носителя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**(5)**|Запустите **spPowerPivot.msi** для установки поставщиков данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] средство настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] коллекции и расписание обновления данных.|  
|**(6)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**(7)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
 ![Параметры SharePoint](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "параметры SharePoint") [отправки отзывов и контактных данных через Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
###  <a name="bkmk_powerpivot_sharepoint2013_1server"></a> Развертывание PowerPivot для SharePoint 2013 одного сервера  
 Развертывание одиночного сервера полезно для тестирования, но не рекомендуется для производственных целей.  
  
 На следующей схеме показана компоненты, которые являются частью одного сервера [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывания.  
  
 ![PowerPivot для развертывания сервера SharePoint одним](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "PowerPivot для SharePoint одного сервера развертывания")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
|**(4)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_2server"></a> Развертывание PowerPivot для SharePoint 2013 два сервера  
 В следующем двухсерверном развертывании компонент SQL Server Database Engine и [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint запустите на сервере, отдельном от SharePoint. Для SharePoint 2013 [!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)] пакет установщика (**spPowerPivot.msi**) устанавливается на сервере SharePoint.  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] расширяет функциональность SharePoint Server 2013 для добавления данных на сервере обработки и обновления, поставщики данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] коллекции и поддержку управления [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книг и книг Excel с расширенными моделями данных.  
  
 Пакет установщика доступен в составе пакета дополнительных компонентов [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Пакет дополнительных компонентов можно загрузить из [!INCLUDE[msCoName](../../includes/msconame-md.md)] центра загрузки Майкрософт по [PowerPivot® Microsoft® SQL Server® 2014 для Microsoft® SharePoint®](http://go.microsoft.com/fwlink/?LinkID=296473) (гиперссылка «http://go.microsoft.com/fwlink/?LinkID=296473"\t «_blank» http://go.microsoft.com/fwlink/?LinkID=296473).  
  
 ![Развертывание сервера в режиме PowerPivot 2 SSAS](../../../2014/analysis-services/media/as-powerpivot-mode-2server-deployment.gif "развертывания сервера службы SSAS режиме PowerPivot 2")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|ЗАПУСТИТЕ **spPowerPivot.msi** для установки поставщиков данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] средство настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] коллекции и расписание обновления данных.|  
|**(4)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**(5)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_3server"></a> Развертывание PowerPivot для SharePoint 2013 три сервера  
 В следующем развертывании трех серверов SQL Server Database Engine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] сервера, работающего в режиме интеграции с SharePoint и SharePoint, каждое выполнение на отдельном сервере. Пакет установщика [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 (spPowerPivot.msi) должен быть установлен на сервере SharePoint.  
  
 ![КАК развертывание сервера в режиме AS PowerPivot 3](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "как развертывание сервера в режиме AS PowerPivot 3")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|ЗАПУСТИТЕ spPowerPivot.msi для установки поставщиков данных, средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и указания времени обновления данных.|  
|**(4)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**(5)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a> PowerPivot для развертывания на одном сервере SharePoint 2013 и служб Reporting Services  
 Развертывание одиночного сервера полезно для тестирования, но не рекомендуется для производственных целей.  
  
 ![Режим интеграции служб SSAS и SSRS с SharePoint 1 развертывания сервера](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "SSAS и SSRS с SharePoint режим 1 развертывания сервера")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|Приложение службы PowerPivot. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|Приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|**(4)**|Установите надстройку служб Reporting Services для SharePoint с установочного носителя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**(5)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
|**(6)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a> PowerPivot для SharePoint 2013 и службы Reporting Services развертывание двух серверов  
 В следующем двухсерверном развертывании ядро СУБД SQL Server и сервер Analysis Services в режиме интеграции с SharePoint работают на сервере, отдельном от SharePoint. PowerPivot для SharePoint 2013 пакет установщика **(spPowerPivot.msi)** должна выполняться на сервере SharePoint.  
  
 ![Службы SSAS и развертывание сервера в режиме интеграции с SharePoint 2 SSRS](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "SSAS и развертывание сервера в режиме интеграции с SharePoint 2 SSRS")  
  
|||  
|-|-|  
|**(1)**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**(2)**|Приложение службы PowerPivot. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**(3)**|Приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|**(4)**|Установите надстройку служб Reporting Services для SharePoint с установочного носителя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**(5)**|ЗАПУСТИТЕ файл **spPowerPivot.msi** для установки поставщиков данных, средства настройки PowerPivot, коллекции PowerPivot и обновления данных по расписанию.|  
|**(6)**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**(7)**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
##  <a name="bkmk_example_deployments_2010"></a> Образцовые топологии развертывания SharePoint 2010  
 На следующей диаграмме показано, какие службы и поставщики работают на каждом из уровней. Обратите внимание, что диаграмма включает несколько встроенных служб. Эти службы необходимы для поддержки некоторых сценариев SQL Server BI. Службы Excel Services, Secure Store и Claims to Windows Token Service либо необходимы, либо рекомендуются для поддержки работы PowerPivot для SharePoint или служб Reporting Services в SharePoint. Кроме того, для поддержки некоторых сценариев доступа к данным PowerPivot необходимы поставщики MSOLAP OLE DB и службы ADO.NET. При необходимости службы Analysis Services можно установить на уровень данных, если требуется построить [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] отчеты на основе табличной модели баз данных, размещенных за пределами SharePoint.  
  
 ![Диаграмма логической архитектуры](../../../2014/sql-server/install/media/sql11bisetup.gif "диаграмма логической архитектуры")  
  
##  <a name="bkmk_sharepoint2010_1server"></a> Развертывание одного сервера  
 Все компоненты сервера, включая уровень данных, можно установить на одном компьютере. Такая конфигурация развертывания полезна при ознакомлении с ПО или при разработке пользовательских приложений, включающих службы Reporting Services в режиме SharePoint. Это развертывание является наиболее простым в настройке. Поскольку все компоненты устанавливаются на одном и том же компьютере, требуется также наименьшее количество лицензий. Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] и компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] устанавливаются как однолицензионная копия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Чтобы установить все компоненты на одиночный сервер, последовательно установите службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] на один и тот же физический сервер. Инструкции по настройке отдельного сервера см. в разделе [контрольный список развертывания: службы Reporting Services, Power View и PowerPivot для SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).  
  
##  <a name="bkmk_sharepoint2010_2server"></a> Двухуровневое развертывание  
 Двухуровневое развертывание обычно включает установку SharePoint Server 2010 на один компьютер и компонент SQL Server Database Engine на второй компьютер. Перемещение уровня данных на выделенный сервер — это наиболее типичная конфигурация двухкомпьютерной фермы. В двухуровневой ферме, как установить [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] на сервере SharePoint. Все веб-службы на сервере, обслуживающем клиентские запросы, и общие службы на уровне приложений эксплуатируются на одном и том же физическом сервере. Шаги по установке в двухуровневой конфигурации очень похожи на установку на отдельном сервере: службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] последовательно устанавливаются на одном и том же физическом сервере.  
  
##  <a name="bkmk_sharepoint2010_3server"></a> Трехуровневое развертывание  
 В трехуровневом развертывании обычно отделяют службы клиентского веб-интерфейса от приложений, интенсивно использующих память. В этой топологии установки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] на сервере приложений. Веб-службы, выполняющиеся на клиентском веб-интерфейсе, устанавливаются как решения, которые развернуты в качестве приложений в ферме в процессе настройки сервера, как задача после установки. На следующей диаграмме проиллюстрировано трехуровневое развертывание.  
  
 ![Топология из пяти серверов 3](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "топологических сервер 3")  
  
##  <a name="bkmk_sharepoint2010_scaleserver"></a> Трехуровневое масштабное развертывание  
 Эта топология иллюстрирует масштабное развертывание, при котором одна и та же общая служба выполняется на нескольких серверах, что позволяет обслуживать большое количество запросов и предоставлять дополнительные мощности по обработке данных PowerPivot или отчетов служб Reporting Services. На нижеследующей диаграмме показаны три кластера серверов приложений, в каждом из которых в различных сочетаниях выполняются общие службы. В среде SharePoint функции обнаружения и проверки доступности служб встроены в ферму. Балансировка загрузки нескольких физических серверов, на которых выполняется одно и то же приложение общей службы, является частью архитектуры общих служб.  
  
 При развертывании многосерверной фермы следуйте инструкциям, приведенным в статье по SharePoint: [Несколько серверов в трехуровневой ферме (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?linkID=219834).  
  
 ![Топология из пяти серверов 5](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "топологических сервера 5")  
  
## <a name="see-also"></a>См. также  
 [Установка в режиме интеграции с SharePoint служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Установка PowerPivot для SharePoint 2013](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)   
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  