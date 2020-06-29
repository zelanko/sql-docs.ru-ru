---
title: Редактор преобразования «Выборка строк» (страница «выборка») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql12.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3e75cb6d7c0e8838dc9e56241424bbf7dfe2755
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422831"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a>Редактор преобразования «Выборка строк» (страница выборки)
  Диалоговое окно **Редактор преобразования «Выборка строк»** используется для деления на части входных данных в выборке, используя указанное количество строк. Это преобразование разделяет входные данные на два отдельных вывода.  
  
 Дополнительные сведения о преобразовании «Выборка строк» см. в разделе [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Число строк**  
 Задайте количество строк из входных данных для использования в качестве выборки.  
  
 Значение этого свойства можно задать с помощью выражения свойства.  
  
 **Имя выхода выборки**  
 Задайте уникальное имя выхода, содержащего строки выборки. Указанное имя будет отображаться в конструкторе служб SSIS.  
  
 **Имя вывода невыбранных элементов**  
 Задает уникальное имя выхода, который содержит строки, исключенные из выборки. Указанное имя будет отображаться в конструкторе служб SSIS.  
  
 **Использовать следующее начальное значение**  
 Задайте начальное значение выборки для генератора случайных чисел, который преобразование использует для создания выборки. Рекомендуется только для разработки и тестирования. Если начальное значение выборки не задано, преобразование использует счетчик сигналов времени Microsoft Windows.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Преобразование "Процентная выборка"](data-flow/transformations/percentage-sampling-transformation.md)  
  
  
