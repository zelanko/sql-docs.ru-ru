---
title: "Сначала конструирование первой или данных, при создании в мобильные отчеты служб Reporting Services | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7b355fa-312b-4074-bc9b-776269d4fb51
caps.latest.revision: 17
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8cf203f17ac149825e0e4d79ed7f6f6041700ae4
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="design-first-or-data-first-when-creating-in-reporting-services-mobile-reports"></a>Design first or data first when creating in Reporting Services mobile reports
  
С помощью [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)]в рабочей области конструирования с настраиваемыми строками и столбцами сетки, а также гибкими элементами мобильных отчетов можно быстро создать мобильные отчеты, которые масштабируются в соответствии с любым размером экрана.   
  
При создании мобильных отчетов можно выбрать один из двух основных подходов: "сначала данные" или "сначала конструирование". [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] поддерживает оба подхода.   
  
## <a name="design-first"></a>Сначала конструирование  
  
На следующем рисунке показаны компоненты режима макета [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] .   
  
![SS_MRP_LayoutTab](../../reporting-services/mobile-reports/media/ss-mrp-layouttab.png)  
  
При использовании подхода "сначала конструирование" создается макет мобильного отчета, при этом данные не импортируются. Это оптимальный вариант, если вы не уверены, отформатированы ли данные надлежащим образом. Без реальных данных элементы коллекции автоматически привязываются к созданным смоделированным данным, которые можно экспортировать и использовать в качестве шаблона для описания необходимых данных.  
  
## <a name="data-first"></a>Сначала данные  
При использовании подхода "сначала данные" необходимо импортировать все необходимые данные, а затем сконструировать мобильный отчет и задать свойства данных в элементах мобильного отчета. Этот подход дает возможность подключить каждый элемент к реальным данным при добавлении в макет. При использовании подхода "сначала данные" убедитесь, что реальные данные отформатированы надлежащим образом для использования с [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)].   
  
 На следующем рисунке показаны все компоненты представления данных [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] .  
  
![SS_MRP_DataTab](../../reporting-services/mobile-reports/media/ss-mrp-datatab.png)  
  
### <a name="see-also"></a>См. также:  
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  См. статью [Просмотр мобильных отчетов SQL Server и ключевых показателей эффективности в приложении для iPad](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI для iOS).  
-  См. статью [Просмотр мобильных отчетов SQL Server и ключевых показателей эффективности в приложении для iPhone](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI для iOS).  
  
  
  
  


