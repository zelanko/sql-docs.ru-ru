---
title: Свойства пути | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ca263b866fb6d5d7ceb6352f708f387d79cad4f7
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423471"
---
# <a name="path-properties"></a>Свойства пути
  Объекты потока данных в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] объектной модели имеют общие свойства и пользовательские свойства на уровне компонента, входов и выходов, а также входных и выходных столбцов. Многие свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
 Этот раздел содержит список и описание пользовательских свойств путей, соединяющих объекты потоков данных.  
  
## <a name="path-properties"></a>Свойства пути  
 В модели объектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] путь, соединяющий компоненты потока данных, реализует интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>.  
  
 В следующей таблице показаны настраиваемые свойства путей в потоке данных. Подсистема обработки потока данных также назначает значения дополнительным, доступным только для чтения, свойствам, которые здесь не перечислены.  
  
|Имя свойства|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|PathAnnotation|Integer (перечисление)|Значение показывает, следует ли отображать описание рядом с путем в области конструктора. Допустимые значения — `AsNeeded`, `SourceName`, `PathName` и `Never`. Значение по умолчанию — `AsNeeded`.|  
|DestinationName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|Вход, связанный с путем.|  
|SourceName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|Выход, связанный с путем.|  
  
## <a name="see-also"></a>См. также  
 [Пути Integration Services](data-flow/integration-services-paths.md)   
 [Общие свойства](../../2014/integration-services/common-properties.md)   
 [Пользовательские свойства преобразования](data-flow/transformations/transformation-custom-properties.md)   
 [Свойства потока данных, которые можно задавать с помощью выражений](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
