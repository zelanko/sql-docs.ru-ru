---
title: "Создание отчета с вкладками мобильных устройств с помощью детализации | Мобильные отчеты служб Reporting | Документы Microsoft"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4d5d80d-370a-4a6d-8b76-698bd5ba5ba6
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6554f808c19540d2a3b7cbe3fdf4e86c5fe7a357
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-tabbed-mobile-report-by-using-drillthrough"></a>Создание отчета с вкладками мобильных устройств с помощью детализации
Вы можете научиться создавать мобильных отчет [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , который выглядит и работает как отчет с вкладками, с помощью детализации и параметров.

Например, в этом отчете датчики в верхней части играют роль вкладок. При выборе датчика транспортировки (Transportation) остальная часть диаграммы фильтруется по данным о транспортировке.

![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/tabbed-mobile-report-web-viewer-transportation-complete.png)

В действительности это набор из пяти отдельных отчетов, в каждом из которых есть свой параметр для фильтрации отчета в соответствии с датчиком, выбранным в верхней части отчета. Сначала создайте все пять отчетов, а затем для каждой из пяти отчетов, внесенные четыре других датчиков в детализация четыре отчета.

Ниже приведены шаги для этого примера.

## <a name="create-the-basic-report"></a>Создание простого отчета

1. Создайте отчет с именем "Продажи" и с пятью следующими датчиками.

    * Продажи
    * Транспортировка
    * Топливо
    * Память
    * Прочие расходы

   ![01-продажи Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/01-sales-mobile-report-publisher.png)
    
2. Задать **акцент** для **на** датчиков продаж, поэтому он будет выполнено сравнение с остальной части отчета — в этом случае белого на черный.

    ![01a-Sales-Accent-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/01a-sales-accent-mobile-report-publisher.png)
    
3. Сохранить его для [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] сервера отчетов.

## <a name="make-copies-of-the-report"></a>Создавать копии отчета

1. Создайте четыре копии отчета продаж и назовите их. 

    * Транспортировка
    * Топливо
    * Память
    * Прочие расходы

3. Сохранить их, чтобы [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] сервера отчетов.

## <a name="set-the-gauge-as-a-drillthrough"></a>Значение датчика как детализации

В этом разделе необходимо задать датчиков (кроме датчика продаж) в качестве детализации до его соответствующих отчетов.

1. Выберите Транспортировка датчика в отчет Sales.

    ![02-Sales-CREATE-DrillThrough-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/02-sales-create-drillthrough-mobile-report-publisher.png)

2. С **макета** в выбранной вкладкой **визуальные свойства** области выберите **детализации целевой**.

3. Выберите **мобильного отчета**.

4. Найдите и выберите отчет, который будет иметь место назначения для детализации — в этом случае «Финансы - транспорт».

    ![03-Sales-SELECT-Dashboard-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/03-sales-select-dashboard-mobile-report-publisher.png)

5. В **настроить целевой отчет**, выберите параметр для фильтрации отчета и выбрать **применить**.

   ![04-Sales-Apply-Parameters-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/04-sales-apply-parameters-mobile-report-publisher.png)
   
6. Повторите эти шаги для каждого из других датчиков в отчете продаж. 

## <a name="set-the-gauges-for-the-other-reports"></a>Задать датчиков для других отчетов

1.  Откройте отчет Транспортировка сделать датчика продаж детализированный отчет Sales, а остальных трех датчики как детализация на их соответствующие отчеты.

2. Находясь в отчете транспортировки, задайте **диакритических знаков** Транспортировка датчиков для **на**, сравните с оставшейся части отчета.

3. Повторите эти шаги для отчетов топливо, хранения и прочие расходы. 

## <a name="view-the-report-in-the-web-portal"></a>Просмотр отчета в веб-портале

1. Последовательно выберите пункты [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] сервером отчетов, а затем откройте один из отчетов. 

2. Обратите внимание, что каждый из датчики значок детализации в правом верхнем углу.

    ![Web-Viewer-drillthrough-icon-mobile-report-builder](../../reporting-services/mobile-reports/media/web-viewer-drillthrough-icon-mobile-report-builder.png)

3. Выберите один из индикаторов, чтобы перейти к отчету, отфильтрованы, чтобы данные этого датчика.

   ![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/06-mobile-report-web-viewer-transportation.png)

### <a name="see-also"></a>См. также:
    
* [Добавление параметров в мобильный отчет](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)
* [Добавление детализации из мобильного отчета в другие мобильные отчеты или URL-адреса](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)




  


