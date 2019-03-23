---
title: Свойства пути | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b0ddc29ca163d17a812c14251c60b512828a5b3e
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58386661"
---
# <a name="path-properties"></a>Свойства пути
  Объекты потока данных в объектной модели служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] обладают общими свойствами и пользовательскими свойствами на уровне компонента, входами и выходами, а также входными и выходными столбцами. Многие свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
 Этот раздел содержит список и описание пользовательских свойств путей, соединяющих объекты потоков данных.  
  
## <a name="path-properties"></a>Свойства пути  
 В модели объектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] путь, соединяющий компоненты потока данных, реализует интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>.  
  
 В следующей таблице показаны настраиваемые свойства путей в потоке данных. Подсистема обработки потока данных также назначает значения дополнительным, доступным только для чтения, свойствам, которые здесь не перечислены.  
  
|Имя свойства|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|PathAnnotation|Integer (перечисление)|Значение показывает, следует ли отображать описание рядом с путем в области конструктора. Допустимые значения — `AsNeeded`, `SourceName`, `PathName` и `Never`. Значение по умолчанию — `AsNeeded`.|  
|DestinationName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|Вход, связанный с путем.|  
|SourceName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|Выход, связанный с путем.|  
  
## <a name="see-also"></a>См. также  
 [Пути служб Integration Services](data-flow/integration-services-paths.md)   
 [Common Properties](../../2014/integration-services/common-properties.md)   
 [Пользовательские свойства преобразования](data-flow/transformations/transformation-custom-properties.md)   
 [Свойства потока данных, которые можно задавать с помощью выражений](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
