---
title: Редактор преобразования выборки в процентах | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- Percentage Sampling Transformation Editor
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 70e9b290c9d797e6471dc198da7a6299739c0be3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194071"
---
# <a name="percentage-sampling-transformation-editor"></a>редактор преобразования «Процентная выборка»
  Используйте диалоговое окно **Редактор преобразования «Процентная выборка»** для выборки части входных данных по заданному проценту строк. Это преобразование разделяет входные данные на два отдельных вывода.  
  
 Дополнительные сведения о преобразовании «Процентная выборка» см. в разделе [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Процент строк**  
 Задает процент строк во входных данных для использования в качестве выборки.  
  
 Значение этого свойства можно задать с помощью выражения свойства.  
  
 **Имя выхода выборки**  
 Задайте уникальное имя выхода, содержащего строки выборки. Это имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Имя вывода невыбранных элементов**  
 Задает уникальное имя выхода, который содержит строки, исключенные из выборки. Это имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Использовать следующее начальное значение**  
 Задайте начальное значение выборки для генератора случайных чисел, который преобразование использует для создания выборки. Рекомендуется только для разработки и тестирования. Если начальное значение выборки не задано, преобразование использует счетчик тактов Microsoft Windows.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Преобразование "Выборка строк"](data-flow/transformations/row-sampling-transformation.md)  
  
  