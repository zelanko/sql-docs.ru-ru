---
title: Conditional Split Transformation Editor | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
caps.latest.revision: 32
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5c2d37db0ef10e8bae5e6fded476ca43e50c61bb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164785"
---
# <a name="conditional-split-transformation-editor"></a>редактор преобразования «Условное разбиение»
  Диалоговое окно **Редактор преобразования «Условное разбиение»** используется для создания выражений, определения порядка, в котором производится вычисление выражений, а также для именования выходных данных условных разбиений. В этом диалоговом окне вызываются математические, строковые функции, функции даты и времени, а также операторы, которые можно использовать при построении выражений. Первое условие, значение которого вычисляется как TRUE, определяет вывод, на который направляется строка.  
  
> [!NOTE]  
>  Преобразование «Условное разбиение» направляет каждую входную строку только на один вывод. При введении нескольких условий преобразование направляет каждую строку на первый вывод, для которого условие имеет значение TRUE, и не учитывает последующие условия для данной строки. При необходимости последовательной проверки выполнения нескольких условий может потребоваться объединить в потоке данных несколько преобразований «Условное разбиение».  
  
 Дополнительные сведения о редакторе преобразований "Условное разбиение" см. в разделе [Преобразование "Условное разбиение"](data-flow/transformations/conditional-split-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Порядок**  
 Выберите строку и с помощью расположенных справа клавиш-стрелок измените порядок, в соответствии с которым будут оцениваться выражения.  
  
 **Имя вывода**  
 Укажите имя вывода. По умолчанию, используется нумерованный список вариантов, однако можно выбрать любое уникальное имя для описания.  
  
 **Условие**  
 Введите выражение или постройте его, перетаскивая элементы из списка доступных столбцов, переменных, функций и операторов.  
  
 Значение этого свойства можно задать с помощью выражения свойства.  
  
 **См. также**: [Выражения служб Integration Services (SSIS)](expressions/integration-services-ssis-expressions.md), [Операторы (выражение служб SSIS)](expressions/operators-ssis-expression.md) и [Функции (выражение служб SSIS)](expressions/functions-ssis-expression.md).  
  
 **Имя выхода по умолчанию**  
 Введите имя вывода по умолчанию или используйте имя, установленное по умолчанию.  
  
 **Настройка вывода ошибок**  
 Укажите способ обработки ошибок в диалоговом окне [Настройка вывода ошибок](../../2014/integration-services/configure-error-output.md) .  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Разбиение набора данных с помощью преобразования "Условное разбиение"](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
