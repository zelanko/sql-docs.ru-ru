---
title: "Добавление параметров для мобильных отчетов | Службы Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 11/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 113cb057-deec-40eb-abc8-f35d3900eaa6
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6fad62a6549f4b9752bde07e39f53175768a68cb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="add-parameters-to-a-mobile-report--reporting-services"></a>Добавление параметров в мобильный отчет | Службы Reporting Services
Вы можете создать мобильный отчет [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с параметрами, которые позволят вам и адресатам отчетов фильтровать данные в этих отчетах. Отчеты с параметрами могут также служить объектом [детализации из исходного отчета](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md). 

Чтобы создать мобильный отчет, необходимо начать с общего набора данных, имеющего хотя бы один параметр. Дополнительные данные о создании параметров в общем наборе данных см. [здесь](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  

После добавления параметров в мобильный отчет можно создать URL-адрес, чтобы [открыть отчет с параметрами строки запроса](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md).

1. На верхней панели веб-портала [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] выберите **Создать** > **Мобильный отчет**.  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. В левом верхнем углу выберите вкладку **Данные** в [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)].   
  
3. Щелкните **Добавить данные**в правом верхнем углу.  
  
4. Выберите пункт **Сервер отчетов**, а затем выберите сервер.  
  
5. Перейдите к общим наборам данных на сервере и выберите набор данных с параметрами.  
  
   В представлении сетки набор данных будет содержать данные. Зеленый круг со скобками **{ }** обозначает набор данных с параметром.  
     
   ![SSMRP_PforParam](../../reporting-services/mobile-reports/media/ssmrp-pforparam.png)  
  
6. Щелкните символ на вкладке и выберите пункт **Парам {}**.  
  
   ![SSMRP_ParamWheel](../../reporting-services/mobile-reports/media/ssmrp-paramwheel.png)  
  
7. Выберите элемент отчета, который будет передавать в параметр значения.  
  
   ![SSMRP_SetParam](../../reporting-services/mobile-reports/media/ssmrp-setparam.png)  
     
8. Выберите **Просмотр** , чтобы увидеть, как будет выглядеть отчет. В этом отчете список выбора использует параметра Category.

   ![sql-server-mobile-report-publisher-Selection-List-View-No-Selection](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-view-no-selection.png) 
   
9. При выборе значения из списка выбора отчет фильтруется по этому значению, в данном случае это Accessories.

   ![sql-server-mobile-report-publisher-Selection-List-Category-Selected](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-category-selected.png)   
  
### <a name="see-also"></a>См. также:  
-  [Открытие мобильного отчета с определенными параметрами строки запроса](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md)
-  [Добавление детализации из мобильного отчета в другие мобильные отчеты или URL-адреса](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)
-  [Создание общего или внедренного набора данных](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
  
  


