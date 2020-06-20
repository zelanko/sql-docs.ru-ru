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
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b4d3e00998aefefe228b0bf537fa34e25410695c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964534"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a>Редактор преобразования «Выборка строк» (страница выборки)
  Диалоговое окно **Редактор преобразования «Выборка строк»** используется для деления на части входных данных в выборке, используя указанное количество строк. Это преобразование разделяет входные данные на два отдельных вывода.  
  
 Дополнительные сведения о преобразовании «Выборка строк» см. в разделе [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md).  
  
## <a name="options"></a>Варианты  
 **Число строк**  
 Задайте количество строк из входных данных для использования в качестве выборки.  
  
 Значение этого свойства можно задать с помощью выражения свойства.  
  
 **Имя выхода выборки**  
 Задайте уникальное имя выхода, содержащего строки выборки. Указанное имя будет отображаться в конструкторе служб SSIS.  
  
 **Имя вывода невыбранных элементов**  
 Задает уникальное имя выхода, который содержит строки, исключенные из выборки. Указанное имя будет отображаться в конструкторе служб SSIS.  
  
 **Использовать следующее начальное значение**  
 Задайте начальное значение выборки для генератора случайных чисел, который преобразование использует для создания выборки. Рекомендуется только для разработки и тестирования. Если начальное значение выборки не задано, преобразование использует счетчик сигналов времени Microsoft Windows.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [преобразование «Процентная выборка»](data-flow/transformations/percentage-sampling-transformation.md)  
  
  
