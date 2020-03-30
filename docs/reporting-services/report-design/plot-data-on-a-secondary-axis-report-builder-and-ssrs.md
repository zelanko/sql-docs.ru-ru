---
title: Построение данных на вспомогательной оси (построитель отчетов) | Документация Майкрософт
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b53f514104032f55dcdbc88986f8e2679ecd5700
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "77082371"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a>Построение данных на вспомогательной оси (построитель отчетов и службы SSRS)

Диаграмма имеет оси двух типов: основную и вспомогательную. Вспомогательная ось полезна при сравнении двух наборов значений с двумя различающимися диапазонами данных с общей категорией.  
  
 Например, предположим, что имеется диаграмма, вычисляющая доходы за 2008 год в зависимости от налогов. В этом случае период времени в течение 2008 года является общим для обоих наборов данных. Однако, если оба ряда построить на одной оси Y, нельзя сделать полезное сравнение, т. к. шкала оси Y оптимизирована для самых больших значений в наборе данных. Если показать доход на первичной оси, а налог на вторичной, можно отобразить каждый ряд на своей собственной оси Y со своей собственной шкалой значений. Ряды продолжают использовать общую ось X.  
  
 Если сравнивается более двух рядов, необходимо использовать другой подход для сравнения и отображения на диаграмме нескольких рядов. Дополнительные сведения см. в разделе [Несколько рядов на диаграмме](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
 Пример этой диаграммы доступен в виде образца отчета. Дополнительные сведения о скачивании этого и других примеров отчетов см. в статье [Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a>Построение ряда на вторичной оси  
  
1.  Щелкните правой кнопкой мыши ряды в диаграмме или поле в области **Значения** , которую нужно отобразить на вспомогательной оси, и выберите пункт **Свойства ряда**. Откроется диалоговое окно **Свойства ряда** .  
  
2.  Перейдите на вкладку **Оси и область диаграммы**и выберите, какую из вторичных осей необходимо включить: ось значений или ось категорий.  

## <a name="next-steps"></a>Дальнейшие действия

[Форматирование меток оси на диаграмме](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
[Указание интервала оси](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
