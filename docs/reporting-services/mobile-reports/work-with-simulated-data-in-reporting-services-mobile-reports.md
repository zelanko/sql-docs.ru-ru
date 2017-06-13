---
title: "Работать с смоделированных данных в мобильных отчетов Reporting Services | Документы Microsoft"
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
ms.assetid: 6baabc36-58fb-4a98-bb9c-c42bafb16d0f
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0eb83717100f70933d2b1fe00bcd19a8a2901f65
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="work-with-simulated-data-in-reporting-services-mobile-reports"></a>Work with simulated data in Reporting Services mobile reports
При размещении элемента коллекции в область конструктора [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] немедленно генерирует смоделированные данные для этого элемента. Эти данные служат для достижения нескольких полезных целей при создании мобильных отчетов.   
  
![SS_MRP_SimDataTreeMapProps](../../reporting-services/mobile-reports/media/ss-mrp-simdatatreemapprops.png)  
  
Смоделированные данные помогают при использовании подхода на основе конструктора для создания мобильных отчетов. Изначальное заполнение элементов смоделированными данными позволяет быстро создавать прототипы мобильных отчетов без необходимости удовлетворять определенные требования к данных. Затем эти мобильные отчеты можно оценить с точки зрения эстетичности и эффективности.  
  
## <a name="create-an-excel-file-with-simulated-data-as-a-template"></a>Создание файла Excel со смоделированными данными как шаблона  
  
Смоделированные данные также предоставляют шаблон, который точно соответствует требованиям к данным конкретного проекта мобильного отчета.   
  
-  В правом верхнем углу представления данных щелкните **Экспортировать все данные** .   
  
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] создает документ Excel, содержащий смоделированные данные, позволяя тем самым быстро заменить фактические данные, готовые к импорту.   
  
## <a name="how-simulated-data-behaves"></a>Как работают смоделированные данные  
  
Смоделированные данные генерируются специально для мобильного отчета, который вы создаете. По мере того, как вы размещаете элементы в области конструктора, связанные смоделированные данные растут и изменяются для обеспечения наиболее удобной работы, практически как с реальными данными. Эта новая функциональная возможность гарантирует, что если в визуализации диаграмм добавить дополнительный ряд или другим способом расширить область одного или нескольких элементов мобильного отчета, то дополнительные поля и функции фильтров будут доступны.  
  
Как уже упоминалось ранее, смоделированные данные можно экспортировать в файл Excel, создав идеальный шаблон данных для связанного мобильного отчета. Вы можете загрузить свои реальные данные в файл Excel и импортировать их обратно в [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)].   
  
Когда все элементы управления привязаны к реальным данным, смоделированные таблицы, которые больше не используются, автоматически удаляются из мобильного отчета. Нельзя удалить смоделированные таблицы, на которые еще ссылаются элементы в области конструктора.  
  
>**Примечание**. Смоделированные данные не увеличивают общее занимаемое мобильным отчетом место, так как они не сериализуются с мобильным отчетом, а генерируются динамически во время выполнения.  
  
### <a name="see-also"></a>См. также:  
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  См. статью [Просмотр мобильных отчетов SQL Server и ключевых показателей эффективности в приложении для iPad](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI для iOS).  
-  См. статью [Просмотр мобильных отчетов SQL Server и ключевых показателей эффективности в приложении для iPhone](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI для iOS).  
  
  
  
  
  


