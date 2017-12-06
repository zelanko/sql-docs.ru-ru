---
title: "Задание цветов диаграммы с помощью палитры (построитель отчетов и службы SSRS) | Документация Майкрософт"
ms.custom: 
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
caps.latest.revision: "6"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 9d4db53a2b9ca10ee294dd248044f5436d1eecc2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs"></a>Задание цветов диаграммы с помощью палитры (построитель отчетов и службы SSRS)
  Цветовую палитру диаграммы можно изменить, выбрав существующую палитру или определив свою. Пользовательские палитры зависят для конкретного отчета.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-colors-on-the-chart-using-a-built-in-color-palette"></a>Изменение цветов диаграммы с помощью встроенной цветовой палитры  
  
1.  Откройте панель «Свойства».  
  
2.  Щелкните диаграмму в области конструктора. На панели «Свойства» отображаются свойства объекта диаграммы.  
  
     В раскрывающемся списке в верхней части панели свойств появляется имя объекта (по умолчанию —**Диаграмма1** ).  
  
3.  На вкладке **Диаграмма** в свойстве Palette выберите из раскрывающегося списка новую палитру.  
  
    > [!NOTE]  
    >  Изменить цвета или их порядок во встроенной палитре нельзя.  
  
### <a name="to-define-your-own-colors-on-the-chart-using-a-custom-color-palette"></a>Определение пользовательских цветов диаграммы с помощью пользовательской цветовой палитры  
  
1.  Откройте панель «Свойства».  
  
2.  Щелкните диаграмму в области конструктора. На панели «Свойства» отображаются свойства объекта диаграммы.  
  
3.  В разделе **Диаграмма** для свойства **Палитра** выберите значение **Пользовательская**.  
  
4.  В области свойства CustomPaletteColors нажмите кнопку изменения коллекции (**…**). Будет открыто окно **Редактор коллекции ReportColorExpression** .  
  
5.  Чтобы добавить цвет, нажмите кнопку **Добавить** . Выберите цвет из раскрывающегося списка или выберите выражение и укажите шестнадцатеричное значение конкретного цвета — например, ff6600 для оранжевого цвета.  
  
     Дополнительные сведения о шестнадцатеричных значениях см. в разделе [Таблица цветов](http://go.microsoft.com/fwlink/?linkid=9258) в MSDN.  
  
6.  Нажмите кнопку **Добавить** , чтобы добавить в палитру еще один цвет.  
  
7.  По завершении нажмите кнопку **ОК**.  
  
 В пользовательской палитре можно менять порядок цветов, чтобы изменить цвета разных рядов диаграммы.  
  
## <a name="see-also"></a>См. также  
 [Форматирование цветов для рядов на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Указание согласованных цветов для нескольких фигурных диаграмм (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
  
