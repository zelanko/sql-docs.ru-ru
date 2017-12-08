---
title: "Занятие 8: Создание ключевых показателей эффективности | Документы Microsoft"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 1c9a041f0effd496d4d339d5389525cb3b530020
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-7-create-key-performance-indicators"></a>Занятие 7. Создание ключевых показателей эффективности
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии мы создадим ключевые показатели эффективности (KPI). KPI используются для измерения производительности значения, определенного *базовой* мерой относительно *целевого* значения, определенного мерой, или абсолютного значения. В клиентских приложения создания отчетов показатели KPI предоставляют бизнесменам быстрый и легкий способ получения обзорных сведений о развитии бизнеса или определении тенденций. Дополнительные сведения см. в разделе [ключевые показатели эффективности](../analysis-services/tabular-models/kpis-ssas-tabular.md).  
  
Предполагаемое время выполнения этого занятия: **15 минут**  
  
## <a name="prerequisites"></a>Предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [Lesson 6: Создание меры](../analysis-services/lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Создание ключевых показателей эффективности  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>Чтобы создать ключевой показатель Эффективности InternetCurrentQuarterSalesPerformance  
  
1.  В конструкторе моделей щелкните **FactInternetSales** таблицу (вкладку).  
  
2.  В сетке мер щелкните пустую ячейку.  
  
3.  В строке формул над таблицей введите следующую формулу: 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IFERROR([InternetCurrentQuarterSales]/[InternetPreviousQuarterSalesProportionToQTD],BLANK())  
    ```

    Эта мера будет служить базовой мерой для KPI.  
  
4.  Щелкните правой кнопкой мыши **InternetCurrentQuarterSalesPerformance** > **создать ключевой показатель Эффективности**.   
  
5.  В диалоговом окне ключевого индикатора производительности (KPI) в **целевой** выберите **абсолютное значение**, а затем введите **1.1**.  
  
7.  В левом (нижнем) поле ползунка введите **1**, а затем в правом (верхнем) поле ползунка введите **1,07**.  
  
8.  На вкладке **Выберите стиль значка**выберите тип значков: ромб (красный), треугольник (желтый), круг (зеленый).
  
    ![как табличных lesson7-ключевого показателя эффективности](../analysis-services/media/as-tabular-lesson7-kpi.png)
    
    > [!TIP]  
    > Обратите внимание, расширяемый **описания** подпись под доступными стилями значков. Используется для ввода описания для различных элементов KPI упростить их идентификацию в клиентских приложениях.  
  
9. Чтобы завершить создание ключевого показателя эффективности, нажмите кнопку **ОК** .  
  
    В сетке мер Обратите внимание на значок рядом с **InternetCurrentQuarterSalesPerformance** мер. Этот значок указывает, что мера служит базовым значением для KPI.  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>Чтобы создать ключевой показатель Эффективности InternetCurrentQuarterMarginPerformance  
  
1.  В сетке мер для **FactInternetSales** таблицы, щелкните пустую ячейку.  
  
2.  В строке формул над таблицей введите следующую формулу:  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  Щелкните правой кнопкой мыши **InternetCurrentQuarterMarginPerformance** > **создать ключевой показатель Эффективности**.  
  
4.  В диалоговом окне ключевого индикатора производительности (KPI) в **целевой** выберите **абсолютное значение**, а затем введите **1.25**.   
  
5.  В поле **Определите пороговые значения состояния**переместите левое (нижнее) поле ползунка так, чтобы в нем отображалось значение **0,8**, а затем переместите правое (верхнее) поле ползунка так, чтобы в нем отображалось значение **1,03**.  
  
6.  На вкладке **Выберите стиль значка**выберите тип значков: ромб (красный), треугольник (желтый), круг (зеленый). Затем нажмите кнопку **OK**.  
  
## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [занятии 8: Создание перспектив](../analysis-services/lesson-8-create-perspectives.md).
  
  
