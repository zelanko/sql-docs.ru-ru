---
title: Задание цветов диаграммы с помощью палитры (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5519384d458fb195e8c1db1420e816c15b17cd15
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43281115"
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
  
## <a name="see-also"></a>См. также:  
 [Форматирование цветов для рядов на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Указание согласованных цветов для нескольких фигурных диаграмм (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
  
