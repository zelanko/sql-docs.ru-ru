---
title: "Преобразование «Условное разбиение» | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.conditionalsplittrans.f1
helpviewer_keywords:
- Conditional Split transformation
- route rows to different outputs [Integration Services]
ms.assetid: 3f8b5825-226f-413c-ba8f-0bb931ca3770
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d5c9ba281713154357344891987131480331f9f0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="conditional-split-transformation"></a>преобразование «Условное разбиение»
  Преобразование «Условное разбиение» может направлять строки данных в различные выходы в зависимости от содержимого данных. Применение преобразования «Условное разбиение» похоже на применение структур выбора CASE в языке программирования. Преобразование производит оценку выражений и на основе результатов направляет строку данных на указанный выход. Это преобразование также предоставляет выход по умолчанию, так что если строка не имеет совпадений, то она направляется в выход по умолчанию.  
  
## <a name="configuration-of-the-conditional-split-transformation"></a>Настройка преобразования «Условное разбиение»  
 Произвести настройку преобразования «Условное разбиение» можно следующими способами.  
  
-   Предоставить выражение, которое вычисляет логическое значение для каждого условия, которое должно быть проверено преобразованием.  
  
-   Указать порядок оценки условий. Порядок имеет большое значение, потому что строка посылается на выход в соответствии с первым условием, имеющим значение TRUE.  
  
-   Задает выход по умолчанию для преобразования. Преобразование требует указания выхода по умолчанию.  
  
 Каждая входная строка может быть послана только на один выход, который является выходом первого условия, имеющего значение TRUE. Например, следующие условия направляют любые строки столбца **FirstName** , которые начинаются с буквы *A* на один выход, строки, начинающиеся с буквы *B* на другой выход, а все остальные строки на выход по умолчанию.  
  
 Выход 1  
  
 `SUBSTRING(FirstName,1,1) == "A"`  
  
 Выход 2  
  
 `SUBSTRING(FirstName,1,1) == "B"`  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] содержат функции и операторы, которые можно использовать для создания выражений, которые оценивают и направляют входные данные. Дополнительные сведения см. в разделе [Выражения служб Integration Services (SSIS)](../../../integration-services/expressions/integration-services-ssis-expressions.md).  
  
 Преобразование «Условное разбиение» содержит пользовательское свойство **FriendlyExpression** . Это свойство может быть обновлено выражением свойства при загрузке пакета. Дополнительные сведения см. в разделах [Использование выражений свойств в пакетах](../../../integration-services/expressions/use-property-expressions-in-packages.md) и [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Это преобразование содержит один вход, один (или более) выход и один выход ошибки.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Условное разбиение»** , см. в разделе [Conditional Split Transformation Editor](../../../integration-services/data-flow/transformations/conditional-split-transformation-editor.md).  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в следующих разделах.  
  
-   [Разбиение набора данных с помощью преобразования «Условное разбиение»](../../../integration-services/data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
-   [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Разбиение набора данных с помощью преобразования «Условное разбиение»](../../../integration-services/data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
## <a name="see-also"></a>См. также  
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
