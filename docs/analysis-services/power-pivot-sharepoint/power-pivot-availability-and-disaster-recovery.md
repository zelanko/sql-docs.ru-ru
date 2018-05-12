---
title: Power Pivot доступности и аварийного восстановления | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2b5a16ac487b52f3592743481e0013b4bf44856
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="power-pivot-availability-and-disaster-recovery"></a>Доступность и аварийное восстановление Power Pivot
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Планы доступности и аварийного восстановления для [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] зависят главным образом от проекта фермы SharePoint, продолжительности простоя, приемлемой для различных компонентов, а также средств и методов работы, которые используются для поддержания доступности SharePoint. В этом разделе содержатся сведения о технологии и диаграммы с примерами топологий, которые следует рассматривать при планировании доступности и аварийного восстановления для развертывания [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 #124; SharePoint 2010|  
  
 **В этом разделе:**  
  
-   [Пример топологии SharePoint 2013 для обеспечения высокой доступности Power Pivot](#bkmk_sharepoint2013)  
  
-   [Пример топологии SharePoint 2010 для обеспечения высокой доступности Power Pivot](#bkmk_sharepoint2010)  
  
-   [Технологии доступности и восстановления базы данных приложения-службы PowerPivot и SQL Server](#bkmk_sql_server_technologies)  
  
-   [Ссылки на дополнительные сведения](#bkmk_more_resources)  
  
##  <a name="bkmk_sharepoint2013"></a> Пример топологии SharePoint 2013 для обеспечения высокой доступности Power Pivot  
 В развертывании [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 предусмотрены более широкие возможности по обеспечению доступности [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . В SharePoint 2013 экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , развернутый в режиме интеграции с SharePoint, который также называют сервером [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , выполняется за пределами фермы SharePoint и может быть установлен на отдельных серверах. Каждый экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме SharePoint регистрируется в службах Excel. Общая служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и приложение службы работают на сервере приложений SharePoint.  
  
 На следующей диаграмме приведен пример развертывания [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013. Этот образец поддерживает высокую доступность служб [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] при условии, что регулярно выполняется резервное копирование баз данных.  
  
 ![доступность PowerPivot в 2013](../../analysis-services/power-pivot-sharepoint/media/ssas-powerpivot-services-2013.png "доступность powerpivot в 2013")  
  
-   **(1)** Серверы клиентского веб-интерфейса. Для установки поставщиков данных на каждом сервере используйте надстройку служб [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013. Дополнительные сведения см. в разделе [Установка или удаление надстройки Power Pivot для SharePoint (SharePoint 2013)](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  
  
-   **(2)** Общая служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] работает **на каждом** сервере приложений и позволяет запускать приложение службы **на нескольких** серверах приложений. Поэтому, если один сервер приложений переходит в режим «вне сети», приложение [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] будет по-прежнему доступно.  
  
-   **(3)** Службы вычислений Excel выполняются на каждом сервере приложений, что позволяет приложению службы работать на разных серверах приложений. Поэтому, если один сервер приложений переходит в режим «вне сети», службы вычислений Excel останутся доступными.  
  
-   **(4)** и **(6)** Экземпляры служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint выполняются на серверах, находящихся за пределами фермы SharePoint. Сюда же входит служба Windows **службы SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)])**. Каждый из этих экземпляров регистрируется в службах Excel **(3)**. Службы Excel обеспечивают балансировку нагрузки запросов к серверам [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Архитектура [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 позволяет иметь несколько серверов для [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , поэтому по мере необходимости можно легко добавлять другие экземпляры. Дополнительные сведения см. в разделе [Управление параметрами модели данных служб Excel (SharePoint Server 2013)](http://technet.microsoft.com/library/jj219780\(v=office.15\).aspx).  
  
-   **(5)** Базы данных SQL Server, используемые для содержимого, конфигурации и в качестве баз данных приложения. Сюда входит и база данных приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . В плане аварийного восстановления следует учитывать уровень базы данных. В этом проекте базы данных выполняются на том же сервере, что и **(4)** один из экземпляров [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . **(4)** и **(5)** также могут находиться на разных серверах.  
  
-   **(7)** Некоторая форма резервного копирования или избыточности базы данных SQL Server.  
  
##  <a name="bkmk_sharepoint2010"></a> Пример топологии SharePoint 2010 для обеспечения высокой доступности Power Pivot  
 Для архитектуры [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 необходимо, чтобы все компоненты [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] работали на одном сервере приложений SharePoint. Сюда входит экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , развернутый в режиме интеграции с SharePoint, и две общие службы, а не одна, как в развертывании SharePoint 2013.  
  
 На следующей диаграмме приведен пример развертывания [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010. Этот образец поддерживает высокую доступность служб [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] при условии, что регулярно выполняется резервное копирование баз данных.  
  
 ![доступность PowerPivot в sharepoint 2010](../../analysis-services/power-pivot-sharepoint/media/ssas-powerpivot-services-2010.png "доступность powerpivot в sharepoint 2010")  
  
-   **(1)** Серверы клиентского веб-интерфейса. Установите поставщики данных на каждом сервере. Дополнительные сведения см. в статье [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
-   **(2)** Две общие службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и **(4)** служба Windows **SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)])** устанавливаются на серверы приложений SharePoint.  
  
     Системная служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] выполняется **на каждом** сервере приложений, что позволяет приложению службы работать **на нескольких** серверах приложений. Если один сервер приложений переходит в режим «вне сети», приложение службы [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] будет по-прежнему доступно.  
  
     Для повышения производительности [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в SharePoint 2010 разверните дополнительные серверы приложений SharePoint с системной службой [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
-   **(3)** Службы вычислений Excel выполняются на каждом сервере приложений, что позволяет приложению службы работать на разных серверах приложений. Поэтому, если один сервер приложений переходит в режим «вне сети», службы вычислений Excel останутся доступными.  
  
-   **(5)** Базы данных SQL Server, используемые для содержимого, конфигурации и в качестве баз данных приложения. Сюда входит и база данных приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . В плане аварийного восстановления следует учитывать уровень базы данных.  
  
-   **(6)** Некоторая форма резервного копирования или избыточности базы данных SQL Server.  
  
##  <a name="bkmk_sql_server_technologies"></a> Технологии доступности и восстановления базы данных приложения-службы PowerPivot и SQL Server  
 Включите базу данных приложения-службы [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] в свое планирование мероприятий по достижению высокого уровня доступности для SharePoint. Имя по умолчанию для этой базы данных: `DefaultPowerPivotServiceApplicationDB-<GUID>`. Ниже приведен перечень технологий доступности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и рекомендации по использованию с базой данных [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Более подробную информацию можно получить в статье [Поддерживаемые варианты обеспечения высокого уровня доступности и аварийного восстановления для баз данных SharePoint (SharePoint 2013)](http://technet.microsoft.com/library/jj841106.aspx).  
  
||Комментарии|  
|-|--------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] в ферме для обеспечения доступности.|Поддерживается, но не рекомендуется. Рекомендуется использовать AlwaysOn в режиме синхронной фиксации.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] в режиме синхронной фиксации|Поддерживается и рекомендуется.|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] асинхронное зеркальное отображение или доставка журналов в другую ферму для аварийного восстановления.|Поддерживается.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] с асинхронной фиксацией аварийного восстановления|Поддерживается|  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Доставка журналов  
  
 Дополнительные сведения о планировании сценария холодного резерва с [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]см. в разделе [Аварийное восстановление PowerPivot](http://social.technet.microsoft.com/wiki/contents/articles/22137.sharepoint-powerpivot-disaster-recovery.aspx).  
  
## <a name="verification"></a>Проверка  
 Руководство и скрипты, с помощью которых можно проверить развертывание [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] до и после цикла аварийного восстановления, см. в разделе [Контрольный список. Использование PowerShell для проверки PowerPivot для SharePoint](../../analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md).  
  
##  <a name="bkmk_more_resources"></a> Ссылки на дополнительные сведения  
  
-   [Поддерживаемые варианты обеспечения высокого уровня доступности и аварийного восстановления для баз данных SharePoint (SharePoint 2013)](http://technet.microsoft.com/library/jj841106.aspx)  
  
-   [Планирование аварийного восстановления (SharePoint Server 2010)](http://technet.microsoft.com/library/ff628971\(v=office.14\).aspx)  
  
-   [Технический документ по резервному копированию и восстановлению облака SQL Server](http://www.microsoft.com/server-cloud/solutions/cloud-backup-recovery.aspx?WT.srch=1&WT.mc_ID=SEM_BING_USEvergreenSearch_Unassigned&CR_CC=Unassigned#fbid=RjU2Nbzu2dT)  
  
-   [Microsoft® SQL Server Backup to Microsoft Windows® Azure®Tool](http://www.microsoft.com/download/details.aspx?id=40740)  
  
 **Содержимое сообщества**  
  
-   [Управление экземплярами служб в SharePoint 2013](http://www.petri.co.il/manage-service-instances-sharepoint-2013.htm)  
  
