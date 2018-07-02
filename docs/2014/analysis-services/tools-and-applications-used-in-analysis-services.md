---
title: Средств и приложений, используемых в службах Analysis Services | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cb258b1d1cc9466d1b1c88255e6edbbb854b5aef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101393"
---
# <a name="tools-and-applications-used-in-analysis-services"></a>Средства и приложения, использующиеся в службах Analysis Services
  Найдите средства и приложения, которые понадобятся вам для создания моделей Analysis Services и управления связанными базами данных в экземпляре Analysis Services.  
  
## <a name="analysis-services-model-designers"></a>Конструкторы моделей Analysis Services  
 Табличные и многомерные модели создаются в шаблонах проектов решения, разработанного в оболочке Visual Studio. Шаблон проекта предоставляет конструкторы для создания моделей, кубов, разрешений и ролей, составляющих решение Analysis Services.  
  
### <a name="download-sql-server-data-tools-for-business-intelligence-ssdt-bi"></a>Скачивание SQL Server Data Tools для Business Intelligence (SSDT-BI)  
 Среда [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] для бизнес-аналитики (SSDT-BI), которая ранее называлась Business Intelligence Development Studio (BIDS), используется для создания моделей служб Analysis Services, отчетов служб Reporting Services и пакетов служб Integration Services. Загрузить SSDT-BI можно из следующих расположений:  
  
-   [Скачать SSDT-BI для Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Скачать SSDT-BI для Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 Если на компьютере установлена прежняя версия SSDT-BI или BIDS, то новая версия устанавливается параллельно с предыдущей. Часто новые и старые версии средств проектирования используются на одной рабочей станции, чтобы можно было работать с проектами и решениями, которые рассчитаны на определенную версию сервера.  
  
> [!NOTE]  
>  Имеется несколько сайтов для загрузки версий SSDT для Visual Studio 2012 и для Visual Studio 2013. Большинство загрузок не содержат шаблоны проектов бизнес-аналитики. С помощью приведенных выше ссылок можно получить правильную версию. Чтобы узнать, установлена ли правильная версия SSDT-BI, проверьте папку шаблонов проектов бизнес-аналитики. Эта папка содержит шаблоны проектов для служб Analysis Services, Reporting Services и Integration Services. В зависимости от способа установки SSDT-BI также может отображаться дополнительный шаблон проекта для баз данных SQL Server.  
  
 ![Новые шаблоны проекта в SSDT](media/ssdt-biprojects.png "Новые шаблоны проекта в SSDT")  
  
## <a name="administrative-tools"></a>Средства администрирования  
  
### <a name="sql-server-management-studio"></a>Среда SQL Server Management Studio  
 Management Studio — это основное средство администрирования для всех функций SQL Server, включая Analysis Services. SQL Server Management Studio является дополнительным компонентом. Если он не отображается вместе с другими приложениями SQL Server на странице "Приложения" в Windows Server 2012, запустите настройку SQL Server, чтобы добавить его в установку.  
  
### <a name="sql-server-profiler"></a>Приложение SQL Server Profiler  
 Хотя он обычно не используется, профилировщик SQL Server предоставляет простой способ мониторинга подключений, выполнения запросов MDX и других операций сервера. Профилировщик SQL Server устанавливается по умолчанию. Его и приложения SQL Server можно найти в разделе "Приложения" в Windows Server 2012.  
  
### <a name="powershell"></a>PowerShell  
 Для выполнения многих административных задач можно использовать команды PowerShell. Подробнее см. в разделе [Analysis Services PowerShell](analysis-services-powershell.md) .  
  
### <a name="community-and-third-party-tools"></a>Средства сообщества и сторонние средства  
 Примеры кодов сообщества см. на [странице CodePlex Analysis Services](http://sqlsrvanalysissrvcs.codeplex.com/) . Рекомендации по сторонним средствам, которые поддерживают Analysis Services см на[Форумах .  
  
  