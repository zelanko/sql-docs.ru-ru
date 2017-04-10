---
title: "редактор преобразования &#171;Процентная выборка&#187; | Microsoft Docs"
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
  - "sql13.dts.designer.percentagesamplingtransformation.f1"
helpviewer_keywords: 
  - "редактор преобразования «Процентная выборка»"
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# редактор преобразования &#171;Процентная выборка&#187;
  Используйте диалоговое окно **Редактор преобразования «Процентная выборка»** для выборки части входных данных по заданному проценту строк. Это преобразование разделяет входные данные на два отдельных вывода.  
  
 Дополнительные сведения о преобразовании «Процентная выборка» см. в разделе [Percentage Sampling Transformation](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md).  
  
## Параметры  
 **Процент строк**  
 Задает процент строк во входных данных для использования в качестве выборки.  
  
 Значение этого свойства можно задать с помощью выражения свойства.  
  
 **Имя выхода выборки**  
 Задайте уникальное имя выхода, содержащего строки выборки. Это имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 **Имя вывода невыбранных элементов**  
 Задает уникальное имя выхода, который содержит строки, исключенные из выборки. Это имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
 **Использовать следующее начальное значение**  
 Задайте начальное значение выборки для генератора случайных чисел, который преобразование использует для создания выборки. Рекомендуется только для разработки и тестирования. Если начальное значение выборки не задано, преобразование использует счетчик тактов Microsoft Windows.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Преобразование «Выборка строк»](../../../integration-services/data-flow/transformations/row-sampling-transformation.md)  
  
  