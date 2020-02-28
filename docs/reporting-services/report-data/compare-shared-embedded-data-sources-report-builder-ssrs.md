---
title: Сравнение общих и внедренных источников данных в построителе отчетов и Reporting Services | Документация Майкрософт
ms.date: 11/18/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 33e257659922e3e0dcf06f559838db0c58f0b18e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "77081792"
---
# <a name="compare-shared-and-embedded-data-sources---report-builder--reporting-services-ssrs"></a>Сравнение общих и внедренных источников данных в построителе отчетов и Reporting Services (SSRS)

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]
 
Вы можете подключаться к данным как с общим, так и с внедренным источником данных. *Общий источник данных* определяется независимо от отчетов. Вы можете использовать его в нескольких отчетах на сервере отчетов или на сайте SharePoint. *Внедренный источник данных* определяется в отчете. Его можно использовать только в этот же отчет. 

 Применение общего источника данных рекомендовано в тех случаях, когда источник данных используется часто. Мы рекомендуем использовать общие источники данных (если возможно). Они облегчают управление отчетами и доступом к ним, а также помогают обеспечить безопасность отчетов и источников данных. Необходимый общий источник данных можно получить, обратившись к системному администратору.  
  
 Внедренный источник данных, также известный, как *источник данных, зависящий от отчета* представляет собой подключение к данным, которое сохраняется в определении отчета. Эти сведения могут использоваться только тем отчетом, в который они внедрены. Внедренные источники данных определяются и управляются с помощью диалогового окна **Свойства источника данных** .  
  
 Различие между общими и внедренными источниками данных состоит в способе создания, хранения и управления.  
  
-   В конструкторе отчетов создайте внедренные или общие источники данных в рамках среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] проекта. Можно выбрать, следует ли использовать их локально для предварительного просмотра или для развертывания их в качестве части проекта на сервере отчетов или сайте SharePoint. Можно использовать пользовательские данные модули, которые были установлены на локальном компьютере и на сервере отчетов или сайте SharePoint, где развертываются отчеты.  
  
     Системные администраторы могут установить и настроить дополнительные модули обработки данных и поставщики данных платформы .NET Framework. Дополнительные сведения см. в разделе [Модули обработки данных и поставщики данных .NET Framework (службы SSRS)](../../reporting-services/report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md).  
  
     Разработчики могут воспользоваться API-интерфейсом <xref:Microsoft.ReportingServices.DataProcessing> для создания модулей обработки данных, работающих с другими типами источников данных.  
  
-   В [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]перейдите на сервер отчетов или веб-сайт SharePoint и выберите общие источники данных или создайте внедренные источники данных в отчете. В [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]невозможно создать общий источник данных. В [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]невозможно использовать пользовательские модули обработки данных.  

## <a name="summary-of-differences"></a>Сводка отличий
  
 В следующей таблице приведены все различия между внедренными и общими источниками данных.  
  
|Описание|Внедренный<br /><br /> Источник данных|Совмещаемая блокировка<br /><br /> Источник данных|  
|-----------------|------------------------------|----------------------------|  
|Подключение к данным внедрено в определение отчета.|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")||  
|Указатель на подключение к данным на сервере ответов внедрен в определение отчета.||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|  
|Управляется на сервере отчетов|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|  
|Необходим для общих наборов данных||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|  
|Необходим для компонентов||![Доступно](../../reporting-services/report-data/media/greencheck.gif "Доступно")|  

## <a name="next-steps"></a>Дальнейшие действия

[Create, Modify, and Delete Shared Data Sources (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)  (Создание, изменение и удаление общих источников данных)  
[Создание и изменение внедренных источников данных](../../reporting-services/report-data/create-and-modify-embedded-data-sources.md)   
[Определение свойств развертывания](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
[Задание учетных данных и сведениях о соединении для источников данных отчета](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
