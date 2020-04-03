---
title: Добавление параметров в мобильный отчет | Службы Reporting Services | Документы Майкрософт
description: Мобильный отчет Reporting Services может содержать параметры, поэтому читатели отчетов могут фильтровать их. Такой отчет также может быть целевым объектом детализации.
ms.date: 07/30/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 113cb057-deec-40eb-abc8-f35d3900eaa6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 41895890a5528a1ddac90a4c9f9eea05d80fac93
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79448292"
---
# <a name="add-parameters-to-a-mobile-report--reporting-services"></a>Добавление параметров в мобильный отчет | Службы Reporting Services
Мобильный отчет [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] можно создать с параметрами, которые позволят получателям отчета фильтровать данные в нем. Отчет с параметрами может также служить объектом [детализации для исходного отчета](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md). 

Чтобы создать мобильный отчет, необходимо начать с общего набора данных, имеющего хотя бы один параметр. Дополнительные данные о создании параметров в общем наборе данных см. [здесь](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md). Мобильные отчеты не поддерживают значение NULL для параметров по умолчанию, поэтому следите за тем, чтобы у параметров по умолчанию не было такого значения.

После добавления параметров в мобильный отчет можно создать URL-адрес, чтобы [открыть отчет с параметрами строки запроса](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md). 

1. На верхней панели веб-портала [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] выберите **Создать** > **Мобильный отчет**.  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. В левом верхнем углу выберите вкладку **Данные** в [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)].   
  
3. Щелкните **Добавить данные**в правом верхнем углу.  
  
4. Выберите пункт **Сервер отчетов**, а затем выберите сервер.  
  
5. Перейдите к общим наборам данных на сервере и выберите набор данных с параметрами.  
  
   В представлении сетки набор данных будет содержать данные. Зеленый круг со скобками **{ }** обозначает набор данных с параметром.  
     
   ![SSMRP_PforParam](../../reporting-services/mobile-reports/media/ssmrp-pforparam.png)  
  
6. Щелкните символ шестеренки на вкладке и выберите пункт **Парам {}** .  
  
   ![SSMRP_ParamWheel](../../reporting-services/mobile-reports/media/ssmrp-paramwheel.png)  
  
7. Выберите элемент отчета, который будет передавать в параметр значения.  
  
   ![SSMRP_SetParam](../../reporting-services/mobile-reports/media/ssmrp-setparam.png)  
     
8. Выберите **Просмотр** , чтобы увидеть, как будет выглядеть отчет. В этом отчете список выбора использует параметра Category.

   ![sql-server-mobile-report-publisher-Selection-List-View-No-Selection](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-view-no-selection.png) 
   
9. При выборе значения из списка выбора отчет фильтруется по этому значению, в данном случае это Accessories.

   ![sql-server-mobile-report-publisher-Selection-List-Category-Selected](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-category-selected.png)   
  
### <a name="see-also"></a>См. также раздел  
-  [Открытие мобильного отчета с определенными параметрами строки запроса](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md)
-  [Добавление детализации из мобильного отчета в другие мобильные отчеты или URL-адреса](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)
-  [Создание общего или внедренного набора данных](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
  
  

