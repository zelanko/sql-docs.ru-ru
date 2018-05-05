---
title: Изменение мер | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8f26ac45b4408f1569302d0ed3975f4629c00d4d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
  
