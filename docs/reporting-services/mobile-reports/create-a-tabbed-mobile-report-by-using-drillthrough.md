---
title: Создание мобильного отчета с вкладками с помощью детализации | Мобильные отчеты Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: mobile-reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c4d5d80d-370a-4a6d-8b76-698bd5ba5ba6
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d3632642114f84855fb1c4e00df810499d23b9d8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-tabbed-mobile-report-by-using-drillthrough"></a>Создание мобильного отчета со вкладками с помощью детализации
Вы можете научиться создавать мобильных отчет [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , который выглядит и работает как отчет с вкладками, с помощью детализации и параметров.

Например, в этом отчете датчики в верхней части играют роль вкладок. При выборе датчика транспортировки (Transportation) остальная часть диаграммы фильтруется по данным о транспортировке.

![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/tabbed-mobile-report-web-viewer-transportation-complete.png)

В действительности это набор из пяти отдельных отчетов, в каждом из которых есть свой параметр для фильтрации отчета в соответствии с датчиком, выбранным в верхней части отчета. Сначала создаются все пять отчетов, а затем для каждого из них в детализацию к другим отчетам вносятся четыре других датчика.

Ниже приводится инструкции для этого примера.

## <a name="create-the-basic-report"></a>Создание простого отчета

1. Создайте отчет с именем "Продажи" и с пятью следующими датчиками.

    * Sales
    * Транспортировка
    * Топливо
    * Память
    * Прочие расходы

   ![01-Sales-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/01-sales-mobile-report-publisher.png)
    
2. Для датчика "Продажи" присвойте свойству **Цвет элементов** значение **Вкл**, чтобы он контрастировал с остальным отчетом. В этом случае это будет белый датчик на белом фоне.

    ![01a-Sales-Accent-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/01a-sales-accent-mobile-report-publisher.png)
    
3. Сохраните его на сервере отчетов [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)].

## <a name="make-copies-of-the-report"></a>Создание копий отчета

1. Создайте четыре копии отчета "Продажи" и присвойте им следующие имена: 

    * Транспортировка
    * Топливо
    * Память
    * Прочие расходы

3. Сохраните их на сервере отчетов [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)].

## <a name="set-the-gauge-as-a-drillthrough"></a>Настройка датчика в качестве детализации

В этом разделе вы настроите каждый датчик (кроме датчика "Продажи") в качестве детализации к соответствующему отчету.

1. В отчете "Продажи" выберите датчик "Транспорт".

    ![02-Sales-Create-DrillThrough-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/02-sales-create-drillthrough-mobile-report-publisher.png)

2. Откройте вкладку **Макет**, а затем на панели **Свойства визуальных элементов** выберите **Целевой объект детализации**.

3. Выберите **Мобильный отчет**.

4. Выберите отчет, который будет целевым для детализации. В данном случае это отчет "Финансы — Транспорт".

    ![03-Sales-Select-Dashboard-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/03-sales-select-dashboard-mobile-report-publisher.png)

5. В окне **Настройка целевого отчета** выберите параметр для фильтрации отчета и нажмите кнопку **Применить**.

   ![04-Sales-Apply-Parameters-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/04-sales-apply-parameters-mobile-report-publisher.png)
   
6. Повторите эти шаги для каждого из остальных датчиков в отчете "Продажи". 

## <a name="set-the-gauges-for-the-other-reports"></a>Настройка датчиков для других отчетов

1.  Откройте отчет "Транспорт", задайте датчик продаж как детализацию к отчету о продажах и остальные датчики как детализацию к соответствующим отчетам.

2. Не закрывая отчет "Транспорт", установите свойство **Цвет элементов** датчика транспортировки в значение **Вкл**, чтобы он отличался от остальной части отчета.

3. Повторите эти действия для отчетов по топливу, складу и прочим расходам. 

## <a name="view-the-report-in-the-web-portal"></a>Просмотр отчета на веб-портале

1. Перейдите на сервер отчетов [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] и откройте один из отчетов. 

2. Обратите внимание на то, что в правом верхнем углу каждого датчика есть значок детализации.

    ![Web-Viewer-drillthrough-icon-mobile-report-builder](../../reporting-services/mobile-reports/media/web-viewer-drillthrough-icon-mobile-report-builder.png)

3. Выберите один из датчиков, чтобы перейти к отчету, отфильтрованному по данным этого датчика.

   ![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/06-mobile-report-web-viewer-transportation.png)

### <a name="see-also"></a>См. также раздел
    
* [Добавление параметров в мобильный отчет](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)
* [Добавление детализации из мобильного отчета в другие мобильные отчеты или URL-адреса](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)




  

