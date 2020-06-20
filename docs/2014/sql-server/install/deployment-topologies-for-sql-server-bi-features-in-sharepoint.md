---
title: Топологии развертывания для функций SQL Server BI в SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 39f76bc7-94e6-4dbc-bfa5-d56f4430bb26
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1ffea6cf93eb1e9e5f137c4151e0f0d9e4d2ca4a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85045752"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>Deployment Topologies for SQL Server BI Features in SharePoint
  В этом разделе описываются типовые топологии для установки компонентов SQL Server Business Intelligence [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] в средах SharePoint 2010 и SharePoint 2013. Например, один сервер и три уровня.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **В этом разделе:**  
  
-   [Примеры топологии развертывания в SharePoint 2013](#bkmk_example_deployments_2013)  
  
    -   [Развертывание трех серверов для случая PowerPivot для SharePoint 2013 и служб Reporting Services](#bkmk_bi_Sharepoint2013_3tier)  
  
    -   [Развертывание в конфигурации с одиночным сервером PowerPivot для SharePoint 2013](#bkmk_powerpivot_sharepoint2013_1server)  
  
    -   [Развертывание двух серверов PowerPivot для SharePoint 2013](#bkmk_powerpivot_sharepoint2013_2server)  
  
    -   [Развертывание трех серверов PowerPivot для SharePoint 2013](#bkmk_powerpivot_sharepoint2013_3server)  
  
    -   [Развертывание одного сервера для случая PowerPivot для SharePoint 2013 и служб Reporting Services](#bkmk_powerpivot_ssrs_sharepoint2013_1server)  
  
    -   [Развертывание двух серверов для PowerPivot для SharePoint 2013 и служб Reporting Services](#bkmk_powerpivot_ssrs_sharepoint2013_2server)  
  
-   [Образцовые топологии развертывания в SharePoint 2010](#bkmk_example_deployments_2010)  
  
    -   [Развертывания в конфигурации с одиночным сервером](#bkmk_sharepoint2010_1server)  
  
    -   [Двухуровневое развертывание](#bkmk_sharepoint2010_2server)  
  
    -   [Трехуровневое развертывание](#bkmk_sharepoint2010_3server)  
  
    -   [Трехуровневое масштабное развертывание](#bkmk_sharepoint2010_scaleserver)  
  
##  <a name="sharepoint-2013-example-deployment-topologies"></a><a name="bkmk_example_deployments_2013"></a>Примеры топологий развертывания SharePoint 2013  
 Режим установки SQL Server **PowerPivot для SharePoint** не зависит от SharePoint. Он не использует объектную модель или интерфейсы SharePoint для поддержки интеграции. Поэтому службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно установить только на компьютере, работающем под управлением Windows Server 2008 R2 или более поздней версии. Это может быть (но необязательно) сервер приложений в ферме SharePoint. Один из шагов настройки — связать службы Excel с сервером, работающим с [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Для балансировки нагрузки и отказоустойчивости рекомендуется установить и зарегистрировать несколько серверов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , работающих в режиме интеграции с SharePoint.  
  
 Для работы в режиме интеграции с ** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint** требуется SharePoint Server 2013 и архитектура приложения службы SharePoint.  
  
 В следующих разделах приведены типичные топологии развертывания:  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-three-server-deployment"></a><a name="bkmk_bi_Sharepoint2013_3tier"></a>PowerPivot для SharePoint 2013 и Reporting Services развертывание трех серверов  
 В следующем трехсерверном развертывании компонент SQL Server Database Engine, сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint, а также SharePoint выполняются на отдельных серверах. Пакет установщика [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013 PowerPivot (**spPowerPivot.msi**) должен запускаться на сервере SharePoint.  
  
 ![Развертывание сервера в режиме интеграции служб SSAS и SSRS с SharePoint 3](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "Развертывание сервера в режиме интеграции служб SSAS и SSRS с SharePoint 3")  
  
|||  
|-|-|  
|**одного**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**открыт**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**3-5**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**четырех**|Установите надстройку служб Reporting Services для SharePoint с установочного носителя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**5.0**|Запустите **spPowerPivot.msi** , чтобы установить поставщики данных, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] средство настройки, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] коллекцию и расписание обновления данных.|  
|**1-6**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**7**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
 ![Параметры SharePoint](../../analysis-services/media/as-sharepoint2013-settings-gear.gif "Параметры SharePoint") [отправляют отзывы и контактные данные через Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) ( https://connect.microsoft.com/SQLServer/Feedback) .  
  
###  <a name="powerpivot-for-sharepoint-2013-single-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_1server"></a>Развертывание с одним сервером PowerPivot для SharePoint 2013  
 Развертывание одиночного сервера полезно для тестирования, но не рекомендуется для производственных целей.  
  
 На следующей диаграмме показаны компоненты, которые входят в состав развертывания [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] одиночного сервера.  
  
 ![Развертывание одиночного сервера PowerPivot для SharePoint](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "Развертывание одиночного сервера PowerPivot для SharePoint")  
  
|||  
|-|-|  
|**одного**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**открыт**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**3-5**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
|**четырех**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
  
###  <a name="powerpivot-for-sharepoint-2013-two-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_2server"></a>Развертывание сервера PowerPivot для SharePoint 2013 2  
 В следующем развертывании двух серверов компонент SQL Server Database Engine и службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint выполняются на сервере, где нет SharePoint. Для SharePoint 2013 пакет установщика [!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)] (**spPowerPivot.msi**) устанавливается на сервере SharePoint.  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)]расширяет SharePoint Server 2013 для добавления обработки обновления данных на стороне сервера, поставщиков данных, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] коллекции и поддержки управления для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книг и книг Excel с расширенными моделями данных.  
  
 Пакет установщика доступен в составе пакета дополнительных компонентов [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Пакет дополнительных компонентов можно скачать из [!INCLUDE[msCoName](../../includes/msconame-md.md)] центра загрузки [майкрософт® SQL Server® 2014 PowerPivot® для Microsoft® SharePoint®](https://go.microsoft.com/fwlink/?LinkID=296473) (Hyperlink " <https://go.microsoft.com/fwlink/?LinkID=296473> " \t "_blank" <https://go.microsoft.com/fwlink/?LinkID=296473> ).  
  
 ![Развертывание сервера в режиме служб SSAS PowerPivot 2](../../analysis-services/media/as-powerpivot-mode-2server-deployment.gif "Развертывание сервера в режиме служб SSAS PowerPivot 2")  
  
|||  
|-|-|  
|**одного**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**открыт**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**3-5**|ЗАПУСТИТЕ **spPowerPivot.msi** для установки поставщиков данных, средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и указания времени обновления данных.|  
|**четырех**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**5.0**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
###  <a name="powerpivot-for-sharepoint-2013-three-server-deployment"></a><a name="bkmk_powerpivot_sharepoint2013_3server"></a>Развертывание сервера PowerPivot для SharePoint 2013 3  
 В следующем трехсерверном развертывании компонент SQL Server Database Engine, сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint, а также SharePoint выполняются на отдельных серверах. Пакет установщика [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 (spPowerPivot.msi) должен быть установлен на сервере SharePoint.  
  
 ![Развертывание сервера в режиме AS PowerPivot 3](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "Развертывание сервера в режиме AS PowerPivot 3")  
  
|||  
|-|-|  
|**одного**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**открыт**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]Приложение службы. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**3-5**|ЗАПУСТИТЕ spPowerPivot.msi для установки поставщиков данных, средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и указания времени обновления данных.|  
|**четырех**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**5.0**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-single-server-deployment"></a><a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a>PowerPivot для SharePoint 2013 и Reporting Services развертывание с одним сервером  
 Развертывание одиночного сервера полезно для тестирования, но не рекомендуется для производственных целей.  
  
 ![Развертывание серверов SSAS и SSRS SharePoint в режиме 1](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "Развертывание серверов SSAS и SSRS SharePoint в режиме 1")  
  
|||  
|-|-|  
|**одного**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**открыт**|Приложение службы PowerPivot. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**3-5**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**четырех**|Установите надстройку служб Reporting Services для SharePoint с установочного носителя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**5.0**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
|**1-6**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
  
###  <a name="powerpivot-for-sharepoint-2013-and-reporting-services-two-server-deployment"></a><a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a>PowerPivot для SharePoint 2013 и Reporting Services развертывания двух серверов  
 В следующем двухсерверном развертывании ядро СУБД SQL Server и сервер Analysis Services в режиме интеграции с SharePoint работают на сервере, отдельном от SharePoint. Пакет установщика PowerPivot для SharePoint 2013 **(spPowerPivot.msi)** должен быть запущен на сервере SharePoint.  
  
 ![Развертывание сервера в режиме интеграции служб SSAS и SSRS с SharePoint 2](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "Развертывание сервера в режиме интеграции служб SSAS и SSRS с SharePoint 2")  
  
|||  
|-|-|  
|**одного**|Приложение службы Excel. Приложение службы создается в процессе установки SharePoint.|  
|**открыт**|Приложение службы PowerPivot. Имя по умолчанию — **Приложение службы PowerPivot по умолчанию**.|  
|**3-5**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**четырех**|Установите надстройку служб Reporting Services для SharePoint с установочного носителя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или из пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**5.0**|ЗАПУСТИТЕ файл **spPowerPivot.msi** для установки поставщиков данных, средства настройки PowerPivot, коллекции PowerPivot и обновления данных по расписанию.|  
|**1-6**|Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Для использования этого сервера настройте **параметры модели данных** приложения служб Excel.|  
|**7**|Базы данных содержимого SharePoint, конфигурации и приложений службы.|  
  
##  <a name="sharepoint-2010-example-deployment-topologies"></a><a name="bkmk_example_deployments_2010"></a>Примеры топологий развертывания SharePoint 2010  
 На следующей диаграмме показано, какие службы и поставщики работают на каждом из уровней. Обратите внимание, что диаграмма включает несколько встроенных служб. Эти службы необходимы для поддержки некоторых сценариев SQL Server BI. Службы Excel Services, Secure Store и Claims to Windows Token Service либо необходимы, либо рекомендуются для поддержки работы PowerPivot для SharePoint или служб Reporting Services в SharePoint. Кроме того, для поддержки некоторых сценариев доступа к данным PowerPivot необходимы поставщики MSOLAP OLE DB и службы ADO.NET. Дополнительно можно установить на уровне данных службу Analysis Services, если предполагается создавать отчеты [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] на основе баз данных табличных моделей, размещенных за пределами SharePoint.  
  
 ![Схема: логическая архитектура](../../../2014/sql-server/install/media/sql11bisetup.gif "Схема: логическая архитектура")  
  
##  <a name="single-server-deployments"></a><a name="bkmk_sharepoint2010_1server"></a>Развертывания на одном сервере  
 Все компоненты сервера, включая уровень данных, можно установить на одном компьютере. Такая конфигурация развертывания полезна при ознакомлении с ПО или при разработке пользовательских приложений, включающих службы Reporting Services в режиме SharePoint. Это развертывание является наиболее простым в настройке. Поскольку все компоненты устанавливаются на одном и том же компьютере, требуется также наименьшее количество лицензий. Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] и компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] устанавливаются как однолицензионная копия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Чтобы установить все компоненты на одиночный сервер, последовательно установите службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] на один и тот же физический сервер. Инструкции по конфигурации изолированного сервера см. в разделе [Контрольный список развертывания: Reporting Services, Power View и PowerPivot для SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).  
  
##  <a name="two-tier-deployment"></a><a name="bkmk_sharepoint2010_2server"></a>Двухстороннее развертывание  
 Двухуровневое развертывание обычно включает установку SharePoint Server 2010 на один компьютер и компонент SQL Server Database Engine на второй компьютер. Перемещение уровня данных на выделенный сервер — это наиболее типичная конфигурация двухкомпьютерной фермы. В двухуровневой ферме на сервере SharePoint устанавливаются служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и служба [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Все веб-службы на сервере, обслуживающем клиентские запросы, и общие службы на уровне приложений эксплуатируются на одном и том же физическом сервере. Шаги по установке в двухуровневой конфигурации очень похожи на установку на отдельном сервере: службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] последовательно устанавливаются на одном и том же физическом сервере.  
  
##  <a name="three-tier-deployment"></a><a name="bkmk_sharepoint2010_3server"></a>Трехуровневой уровень развертывания  
 В трехуровневом развертывании обычно отделяют службы клиентского веб-интерфейса от приложений, интенсивно использующих память. В этой топологии службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] устанавливаются только на сервере приложений. Веб-службы, выполняющиеся на клиентском веб-интерфейсе, устанавливаются как решения, которые развернуты в качестве приложений в ферме в процессе настройки сервера, как задача после установки. На следующей диаграмме проиллюстрировано трехуровневое развертывание.  
  
 ![Топология из трех серверов](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "Топология из трех серверов")  
  
##  <a name="three-tier-scale-out-deployment"></a><a name="bkmk_sharepoint2010_scaleserver"></a>3-уровневое масштабное развертывание  
 Эта топология иллюстрирует масштабное развертывание, при котором одна и та же общая служба выполняется на нескольких серверах, что позволяет обслуживать большое количество запросов и предоставлять дополнительные мощности по обработке данных PowerPivot или отчетов служб Reporting Services. На нижеследующей диаграмме показаны три кластера серверов приложений, в каждом из которых в различных сочетаниях выполняются общие службы. В среде SharePoint функции обнаружения и проверки доступности служб встроены в ферму. Балансировка загрузки нескольких физических серверов, на которых выполняется одно и то же приложение общей службы, является частью архитектуры общих служб.  
  
 При развертывании многосерверной фермы следуйте инструкциям, приведенным в статье по SharePoint: [Несколько серверов в трехуровневой ферме (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834).  
  
 ![Топология из пяти серверов](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "Топология из пяти серверов")  
  
## <a name="see-also"></a>См. также:  
 [Reporting Services установки в режиме интеграции с SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Установка PowerPivot для SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)   
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
