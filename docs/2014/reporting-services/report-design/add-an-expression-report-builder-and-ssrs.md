---
title: Добавление выражения (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 54505266a77c8baee7f39633ebccd0a5ab5708a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106742"
---
# <a name="add-an-expression-report-builder-and-ssrs"></a>Добавление выражения (построитель отчетов и службы SSRS)
  Выражения используются в отчете для определения свойств элементов отчета, фильтров, групп, порядка сортировки, строк подключения и значений параметров. Выражения начинаются со знака равенства (=) и записываются в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Во время выполнения отчета обработчик отчета вычисляет их и применяет результат вычисления к элементам макета отчета.  
  
 Выражения бывают простыми и сложными. Простое выражение ссылается на один элемент встроенной коллекции. Сложные выражения могут содержать константы, операторы, глобальные элементы сбора и вызовы функций. Дополнительные сведения см. в разделе [Выражения (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a>Добавление выражения в текстовое поле  
  
-   В режиме **Конструктор** щелкните текстовое поле в области конструктора, в которое нужно добавить выражение.  
  
    -   В случае простого выражения введите текст выражения в текстовое поле. Например, для поля набора данных «Sales» введите `[Sales]`.  
  
    -   В случае сложного выражения щелкните правой кнопкой мыши текстовое поле и выберите **Выражение**. Откроется диалоговое окно **Выражение** . Введите или интерактивно создайте нужное выражение после знака равенства «=» в панели выражений, а затем нажмите кнопку «ОК».  
  
         Выражение появится в области конструктора в следующем виде: `<<Expr>>`.  
  
## <a name="see-also"></a>См. также:  
 [Форматирование текста и заполнителей (построитель отчетов и службы SSRS)](formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Текстовые поля (построитель отчетов и службы SSRS)](text-boxes-report-builder-and-ssrs.md)   
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры уравнений фильтра &#40;построитель отчетов и SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)   
 [Примеры выражений групп &#40;построитель отчетов и службы SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [&#40;построитель отчетов диалоговом окне "выражение"&#41;](../expression-dialog-box-report-builder.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Добавление кода в отчет &#40;SSRS&#41;](add-code-to-a-report-ssrs.md)  
  
  
