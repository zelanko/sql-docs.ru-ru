---
title: "Вывод значений круговой диаграммы в верхней части диаграммы (построитель отчетов и службы SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# Вывод значений круговой диаграммы в верхней части диаграммы (построитель отчетов и службы SSRS)
По умолчанию в круговых диаграммах отчетов с разбиением на страницы [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] первое значение набора данных отстоит от верхней части диаграммы на 90 градусов. 

![report-builder-pie-chart-start-at-90](../../reporting-services/media/report-builder-pie-chart-start-at-90.png)

*Значения диаграммы начинаются с 90 градусов.*

Можно указать, чтобы первое значение отсчитывалось от верхней части диаграммы. 

![report-builder-pie-chart-start-at-top](../../reporting-services/media/report-builder-pie-chart-start-at-top.png)

*Значения диаграммы начинаются с верхней части диаграммы.*
  
## Отсчет значений круговой диаграммы от верхней части диаграммы  
  
1.  Щелкните круговую диаграмму.  
  
2.  Если панель **Свойства** не отображается, выберите на вкладке **Вид** пункт **Свойства**.  
  
3.  На панели **Свойства** в области **Настраиваемые атрибуты**измените значение **Начальный угол круговой диаграммы** с **0** на **270**.  
  
4.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Теперь первое значение круговой диаграммы отсчитывается от верхней части диаграммы.  
  
## См. также  
 [Форматирование диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Круговые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  