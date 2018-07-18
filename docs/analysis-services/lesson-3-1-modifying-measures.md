---
title: Изменение мер | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 91de9fa781025b79f8aa47ff4e75067fe1045e88
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34017061"
---
# <a name="lesson-3-1---modifying-measures"></a>Занятие 3-1-изменение мер
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
8.  В окне свойств измените свойство **Имя** меры **Unit Price Discount Pct** на **Unit Price Discount Percentage**.  
  
9. На панели **Меры** щелкните **Tax Amt** и измените имя меры на **Tax Amount**.  
  
10. В окне свойств нажмите значок **Автоматически скрыть** , чтобы скрыть окно свойств, а затем нажмите кнопку **Показывать дерево мер** на вкладке панели инструментов **Структура куба** .  
  
11. В меню **Файл** выберите команду **Сохранить все**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Изменение измерения «Заказчик»](../analysis-services/lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a>См. также  
[Определение измерений базы данных](../analysis-services/multidimensional-models/define-database-dimensions.md)  
[Настройка свойств мер](../analysis-services/multidimensional-models/configure-measure-properties.md)  
  
  
  
