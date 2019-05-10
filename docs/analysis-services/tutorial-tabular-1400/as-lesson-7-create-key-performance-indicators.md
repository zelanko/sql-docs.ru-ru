---
title: 'Analysis Services занятие для учебника по 7: Создание ключевых показателей эффективности | Документация Майкрософт'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 5f3b3de71cb60a27613482255556bfbff6bcc8cf
ms.sourcegitcommit: 6193aa9b4967302424270d67c27dbc601ca6849a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877622"
---
# <a name="create-key-performance-indicators"></a>Создание ключевых показателей эффективности

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

В этом занятии вы создадите ключевые показатели эффективности (KPI). Ключевые показатели эффективности используются для оценки производительности значения, определенного *базы* измерения, от *целевой* значения, также определенного мерой или абсолютным значением. В клиентских приложения создания отчетов показатели KPI предоставляют бизнесменам быстрый и легкий способ получения обзорных сведений о развитии бизнеса или определении тенденций. Дополнительные сведения см. в разделе [ключевые показатели эффективности](../tabular-models/kpis-ssas-tabular.md)
  
Предполагаемое время для выполнения этого занятия: **15 минут**  
  
## <a name="prerequisites"></a>предварительные требования  

Эта статья входит в учебник по табличному моделированию, который следует изучать в порядке. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [Занятие 6. Создание мер](../tutorial-tabular-1400/as-lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Создание ключевых показателей эффективности  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>Для создания ключевого показателя Эффективности InternetCurrentQuarterSalesPerformance  
  
1.  В конструкторе моделей щелкните **FactInternetSales** таблицы.  
  
2.  В сетке мер щелкните пустую ячейку.  
  
3.  В строке формул над таблицей введите следующую формулу: 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IF([InternetPreviousQuarterSalesProportionToQTD]<>0,([InternetCurrentQuarterSales]-[InternetPreviousQuarterSalesProportionToQTD])/[InternetPreviousQuarterSalesProportionToQTD],BLANK()) 
    ```

    Эта мера служит базовой мерой для ключевого показателя Эффективности.  
  
4.  В сетке мер щелкните правой кнопкой мыши **InternetCurrentQuarterSalesPerformance** > **создать ключевой показатель Эффективности**.   
  
5.  В диалоговом окне ключевого индикатора производительности (KPI) в **целевой** выберите **абсолютное значение**, а затем введите **1.1**.  
  
7.  В левом (нижнем) поле ползунка введите **1**, а затем в правом (верхнем) поле ползунка введите **1,07**.  
  
8.  На вкладке **Выберите стиль значка**выберите тип значков: ромб (красный), треугольник (желтый), круг (зеленый).
  
    ![as-lesson7-kpi](../tutorial-tabular-1400/media/as-lesson7-kpi.png)
    
    > [!TIP]  
    > Обратите внимание на развертываемую **описания** подпись под доступными стилями значков. Используйте описания для различных элементов KPI, чтобы сделать их более понятными в клиентских приложениях.  
  
9. Чтобы завершить создание ключевого показателя эффективности, нажмите кнопку **ОК** .  
  
    В сетке мер Обратите внимание на значок рядом с полем **InternetCurrentQuarterSalesPerformance** мер. Этот значок указывает, что мера служит базовым значением для KPI.  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>Для создания ключевого показателя Эффективности InternetCurrentQuarterMarginPerformance  
  
1.  В сетке мер для **FactInternetSales** таблицы, щелкните пустую ячейку.  
  
2.  В строке формул над таблицей введите следующую формулу:  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  Щелкните правой кнопкой мыши **InternetCurrentQuarterMarginPerformance** > **создать ключевой показатель Эффективности**.  
  
4.  В диалоговом окне ключевого индикатора производительности (KPI) в **целевой** выберите **абсолютное значение**, а затем введите **1,25**.   
  
5.  В левом (нижнем) поле ползунка, слайдов показывало **0,8**, а затем переместите правое (верхнее) поле ползунка, показывало **1.03**.  
  
6.  На вкладке **Выберите стиль значка**выберите тип значков: ромб (красный), треугольник (желтый), круг (зеленый). Затем нажмите кнопку **OK**.  
  
## <a name="whats-next"></a>Дальнейшие действия

[Занятие 8. Создание перспектив](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).
  
  
