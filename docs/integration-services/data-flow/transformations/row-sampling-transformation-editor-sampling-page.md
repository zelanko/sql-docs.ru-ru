---
title: "Редактор преобразования &#171;Выборка строк&#187; (страница выборки) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1"
  - "sql13.dts.designer.rowsamplingtransformation.f1"
helpviewer_keywords: 
  - "Редактор преобразования «Выборка строк»"
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Редактор преобразования &#171;Выборка строк&#187; (страница выборки)
  Диалоговое окно **Редактор преобразования «Выборка строк»** используется для деления на части входных данных в выборке, используя указанное количество строк. Это преобразование разделяет входные данные на два отдельных вывода.  
  
 Дополнительные сведения о преобразовании «Выборка строк» см. в разделе [Row Sampling Transformation](../../../integration-services/data-flow/transformations/row-sampling-transformation.md).  
  
## Параметры  
 **Число строк**  
 Задайте количество строк из входных данных для использования в качестве выборки.  
  
 Значение этого свойства можно задать с помощью выражения свойства.  
  
 **Имя выхода выборки**  
 Задайте уникальное имя выхода, содержащего строки выборки. Указанное имя будет отображаться в конструкторе служб SSIS.  
  
 **Имя вывода невыбранных элементов**  
 Задает уникальное имя выхода, который содержит строки, исключенные из выборки. Указанное имя будет отображаться в конструкторе служб SSIS.  
  
 **Использовать следующее начальное значение**  
 Задайте начальное значение выборки для генератора случайных чисел, который преобразование использует для создания выборки. Рекомендуется только для разработки и тестирования. Если начальное значение выборки не задано, преобразование использует счетчик сигналов времени Microsoft Windows.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Преобразование «Процентная выборка»](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)  
  
  