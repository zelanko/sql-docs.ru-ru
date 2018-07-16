---
title: Изменение мер | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 447032ab32e222f3827c34020aef612e8125a518
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232384"
---
# <a name="modifying-measures"></a>Изменение мер
  Свойство **FormatString** позволяет определить параметры форматирования, управляющие способом отображения мер для пользователей. В этой задаче предстоит указать свойства форматирования мер валюты и процентов в кубе учебника по службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
### <a name="to-modify-the-measures-of-the-cube"></a>Изменение мер куба  
  
1.  Перейдите на вкладку **Структура куба** конструктора кубов для куба учебника по службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , разверните группу мер **Internet Sales** на панели **Меры** , щелкните правой кнопкой мыши элемент **Order Quantity**и выберите пункт **Свойства**.  
  
2.  В окне свойств нажмите значок канцелярской кнопки **Автоматически скрыть** , чтобы оставить окно свойств постоянно открытым.  
  
     Если окно свойств остается постоянно открытым, изменять свойства нескольких элементов куба проще.  
  
3.  В окне свойств щелкните список **FormatString** и введите **#,#**.  
  
4.  На панели инструментов вкладки **Структура куба** нажмите значок **Показывать сетку мер** слева.  
  
     Сетка просмотра позволяет выбрать несколько мер одновременно.  
  
5.  Выберите следующие меры. Можно выбрать несколько мер. Для этого щелкните каждую из них, удерживая нажатой клавишу CTRL.  
  
    -   **Unit Price**  
  
    -   **Extended Amount**  
  
    -   **Discount Amount**  
  
    -   **Product Standard Cost**  
  
    -   **Total Product Cost**  
  
    -   **Объем продаж**  
  
    -   **Tax Amt**  
  
    -   **Freight**  
  
6.  В окне свойств в списке **FormatString** выберите параметр **Валюта**.  
  
7.  В раскрывающемся списке в верхней части окна свойств (под строкой названия) выберите меру **Процент скидки от стоимости единицы товара**, а затем выберите значение **Процент** в списке **FormatString** .  
  
8.  В окне «Свойства» измените **имя** свойство для **Unit Price Discount Pct** меру `Unit Price Discount Percentage`.  
  
9. В **меры** панели щелкните **Tax Amt** и измените имя меры на `Tax Amount`.  
  
10. В окне свойств нажмите значок **Автоматически скрыть** , чтобы скрыть окно свойств, а затем нажмите кнопку **Показывать дерево мер** на вкладке панели инструментов **Структура куба** .  
  
11. В меню **Файл** выберите команду **Сохранить все**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Изменение измерения Customer](lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a>См. также  
 [Определение измерений базы данных](multidimensional-models/define-database-dimensions.md)   
 [Настройка свойств мер](multidimensional-models/configure-measure-properties.md)  
  
  
