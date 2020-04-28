---
title: Доступность и аварийное восстановление PowerPivot (SQL Server 2014) | Документация Майкрософт
ms.custom: ''
ms.date: 03/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4aaf008c-3bcb-4dbf-862c-65747d1a668c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bf560d489a1631e31f470134d497d3d897f6f35e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175683"
---
# <a name="powerpivot-availability-and-disaster-recovery-sql-server-2014"></a>Доступность и аварийное восстановление PowerPivot (SQL Server 2014)
  Планы доступности и аварийного восстановления для [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] зависят главным образом от проекта фермы SharePoint, продолжительности простоя, приемлемой для различных компонентов, а также средств и методов работы, которые используются для поддержания доступности SharePoint. В этом разделе перечислены технологии и приведены примеры схем топологии, которые следует учитывать при планировании доступности и аварийного восстановления для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] развертывания.

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|

 **В этом разделе:**

-   [Пример топологии SharePoint 2013 для обеспечения высокого уровня доступности PowerPivot](#bkmk_sharepoint2013)

-   [Пример топологии SharePoint 2010 для обеспечения высокого уровня доступности PowerPivot](#bkmk_sharepoint2010)

-   [Технологии доступности и восстановления базы данных приложения-службы PowerPivot и SQL Server](#bkmk_sql_server_technologies)

-   [Ссылки на дополнительные сведения](#bkmk_more_resources)

##  <a name="example-sharepoint-2013-topology-for-powerpivot-high-availability"></a><a name="bkmk_sharepoint2013"></a>Пример топологии SharePoint 2013 для обеспечения высокой доступности PowerPivot
 В развертывании [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 предусмотрены более широкие возможности по обеспечению доступности [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . В SharePoint 2013 экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , развернутый в режиме интеграции с SharePoint, который также называют сервером [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , выполняется за пределами фермы SharePoint и может быть установлен на отдельных серверах. Каждый экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме SharePoint регистрируется в службах Excel. Общая служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и приложение службы работают на сервере приложений SharePoint.

 На следующей диаграмме приведен пример развертывания [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013. Этот образец поддерживает высокую доступность служб [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] при условии, что регулярно выполняется резервное копирование баз данных.

 ![доступность powerpivot в 2013](../media/ssas-powerpivot-services-2013.png "доступность powerpivot в 2013")

-   **(1)** Серверы клиентского веб-интерфейса. Для установки поставщиков данных на каждом сервере используйте надстройку служб [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013. Дополнительные сведения см. в разделе [Установка или удаление надстройки PowerPivot для SharePoint &#40;SharePoint 2013&#41;](../instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).

-   **(2)** Общая служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] работает **на каждом** сервере приложений и позволяет запускать приложение службы **на нескольких** серверах приложений. Поэтому, если один сервер приложений переходит в режим «вне сети», приложение [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] будет по-прежнему доступно.

-   **(3)** Службы вычислений Excel выполняются на каждом сервере приложений, что позволяет приложению службы работать на разных серверах приложений. Поэтому, если один сервер приложений переходит в режим «вне сети», службы вычислений Excel останутся доступными.

-   **(4)** и **(6)** экземпляры [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] служб в режиме интеграции с SharePoint выполняются на серверах за пределами фермы SharePoint, включая службу Windows **SQL Server Analysis Services (PowerPivot)**. Каждый из этих экземпляров регистрируется в службах Excel **(3)**. Службы Excel обеспечивают балансировку нагрузки запросов к серверам [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Архитектура [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 позволяет иметь несколько серверов для [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , поэтому по мере необходимости можно легко добавлять другие экземпляры. Дополнительные сведения см. в разделе [Управление параметрами модели данных служб Excel (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\).aspx).

-   **(5)** Базы данных SQL Server, используемые для содержимого, конфигурации и в качестве баз данных приложения. Сюда входит и база данных приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . В плане аварийного восстановления следует учитывать уровень базы данных. В этом проекте базы данных выполняются на том же сервере, что и **(4)** один из экземпляров [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . **(4)** и **(5)** также могут находиться на разных серверах.

-   **(7)** Некоторая форма резервного копирования или избыточности базы данных SQL Server.

##  <a name="example-sharepoint-2010-topology-for-powerpivot-high-availability"></a><a name="bkmk_sharepoint2010"></a>Пример топологии SharePoint 2010 для обеспечения высокой доступности PowerPivot
 Для архитектуры [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 необходимо, чтобы все компоненты [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] работали на одном сервере приложений SharePoint. Сюда входит экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , развернутый в режиме интеграции с SharePoint, и две общие службы, а не одна, как в развертывании SharePoint 2013.

 На следующей диаграмме приведен пример развертывания [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010. Этот образец поддерживает высокую доступность служб [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] при условии, что регулярно выполняется резервное копирование баз данных.

 ![доступность powerpivot в sharepoint 2010](../media/ssas-powerpivot-services-2010.png "доступность powerpivot в sharepoint 2010")

-   **(1)** Серверы клиентского веб-интерфейса. Установите поставщики данных на каждом сервере. Дополнительные сведения см. в статье [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).

-   **(2)** две [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] общие службы и **(4)** SQL Server Analysis Services службы Windows **(PowerPivot)** установлены на серверах приложений SharePoint.

     Системная служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] выполняется **на каждом** сервере приложений, что позволяет приложению службы работать **на нескольких** серверах приложений. Если один сервер приложений переходит в режим «вне сети», приложение службы [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] будет по-прежнему доступно.

     Для повышения производительности [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в SharePoint 2010 разверните дополнительные серверы приложений SharePoint с системной службой [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .

-   **(3)** Службы вычислений Excel выполняются на каждом сервере приложений, что позволяет приложению службы работать на разных серверах приложений. Поэтому, если один сервер приложений переходит в режим «вне сети», службы вычислений Excel останутся доступными.

-   **(5)** Базы данных SQL Server, используемые для содержимого, конфигурации и в качестве баз данных приложения. Сюда входит и база данных приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . В плане аварийного восстановления следует учитывать уровень базы данных.

-   **(6)** Некоторая форма резервного копирования или избыточности базы данных SQL Server.

##  <a name="powerpivot-service-application-database-and-sql-server-availability-and-recovery-technologies"></a><a name="bkmk_sql_server_technologies"></a>Технологии доступности и восстановления базы данных приложения службы PowerPivot и SQL Server
 Включите базу данных приложения-службы [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] в свое планирование мероприятий по достижению высокого уровня доступности для SharePoint. Имя по умолчанию для этой базы данных: `DefaultPowerPivotServiceApplicationDB-<GUID>`. Ниже приведен перечень технологий доступности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и рекомендации по использованию с базой данных [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Более подробную информацию можно получить в статье [Поддерживаемые варианты обеспечения высокого уровня доступности и аварийного восстановления для баз данных SharePoint (SharePoint 2013)](https://technet.microsoft.com/library/jj841106.aspx).

||Комментарии|
|-|--------------|
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] в ферме для обеспечения доступности.|Поддерживается, но не рекомендуется. Рекомендуется использовать AlwaysOn в режиме синхронной фиксации.|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] в режиме синхронной фиксации|Поддерживается и рекомендуется.|
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] асинхронное зеркальное отображение или доставка журналов в другую ферму для аварийного восстановления.|Поддерживается.|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] с асинхронной фиксацией для аварийного восстановления|Поддерживается|

-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]

-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Доставка журналов

 Дополнительные сведения о планировании сценария холодного резерва с [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]см. в разделе [Аварийное восстановление PowerPivot](https://social.technet.microsoft.com/wiki/contents/articles/22137.sharepoint-powerpivot-disaster-recovery.aspx).

## <a name="verification"></a>Проверка
 Инструкции и сценарии, помогающие проверить [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] развертывание до и после цикла аварийного восстановления, см. в разделе [Контрольный список: использование PowerShell для проверки PowerPivot для SharePoint](../instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md).

##  <a name="links-to-more-information"></a><a name="bkmk_more_resources"></a>Ссылки на дополнительные сведения

-   [Поддерживаемые варианты обеспечения высокого уровня доступности и аварийного восстановления для баз данных SharePoint (SharePoint 2013)](https://technet.microsoft.com/library/jj841106.aspx)

-   [Планирование аварийного восстановления (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628971\(v=office.14\).aspx)




