---
title: Добавление выражения (построитель отчетов) | Документация Майкрософт
description: Сведения о том, как использовать выражения для определения свойств, фильтров и значений элементов отчета в построителе отчетов.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0599aa12178f794d2af40ca40313b6a255e83919
ms.sourcegitcommit: 93e4fd75e8fe0cc85e7949c9adf23b0e1c275465
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2020
ms.locfileid: "84255557"
---
# <a name="add-an-expression-report-builder-and-ssrs"></a>Добавление выражения (построитель отчетов и службы SSRS)
  Выражения используются в отчете для определения свойств элементов отчета, фильтров, групп, порядка сортировки, строк подключения и значений параметров. Выражения начинаются со знака равенства (=) и создаются в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Во время выполнения отчета обработчик отчета вычисляет их и применяет результат вычисления к элементам макета отчета.  
  
 Выражения бывают простыми и сложными. Простое выражение ссылается на один элемент встроенной коллекции. Сложные выражения могут содержать константы, операторы, глобальные элементы сбора и вызовы функций. Дополнительные сведения см. в разделе [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a>Добавление выражения в текстовое поле  
  
-   В режиме **Конструктор** щелкните текстовое поле в области конструктора, в которое нужно добавить выражение.  
  
    -   В случае простого выражения введите текст выражения в текстовое поле. Например, для поля набора данных «Sales» введите `[Sales]`.  
  
    -   В случае сложного выражения щелкните правой кнопкой мыши текстовое поле и выберите **Выражение**. Откроется диалоговое окно **Выражение** . Введите или интерактивно создайте нужное выражение после знака равенства «=» в панели выражений, а затем нажмите кнопку «ОК».  
  
         Выражение появится в области конструктора в следующем виде: `<<Expr>>`.  
  
## <a name="see-also"></a>См. также:  
 [Форматирование текста и заполнителей (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Текстовые поля (построитель отчетов и службы SSRS)](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры уравнений фильтра (построитель отчетов и службы SSRS)](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [Примеры выражений групп &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [Диалоговое окно "Выражение" (построитель отчетов)](https://msdn.microsoft.com/library/e89c4d97-5d41-4b55-8695-79329edac15d)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Добавление кода в отчет (службы SSRS)](../../reporting-services/report-design/add-code-to-a-report-ssrs.md)  
  
  
