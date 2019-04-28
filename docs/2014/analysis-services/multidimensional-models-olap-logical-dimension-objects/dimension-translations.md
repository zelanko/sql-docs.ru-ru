---
title: Переводы измерений | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], translations
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- LCIDs
- translations [Analysis Services], dimensions
ms.assetid: 38fc1e05-2ac9-4816-b52b-dfd19c3a43a2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81e0ecacaa185b9fe520513af57ced3b382a343c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62728530"
---
# <a name="dimension-translations"></a>Переводы измерений
  Перевод — это простой механизм для отображения меток и заголовков на другом языке. Каждый перевод определяется как пара значений: строка с переведенным текстом и значение с идентификатором языка. Переводы доступны для всех объектов в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Значения атрибутов измерений также можно перевести. Клиентское приложение отвечает за поиск языка, заданного пользователем, и отображения на этом языке всех меток и заголовков. Объект может иметь неограниченное число переводов.  
  
 Простой объект <xref:Microsoft.AnalysisServices.Translation> содержит кода языка и переведенного заголовка. Код языка — это значение типа `Integer` с идентификатором языка. Переведенное текстовое обозначение является заголовком.  
  
 В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], перевод измерений — зависящие от языка представление имени измерения, имени объекта [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объекта или одного из его элементов, например заголовка, элемента или уровня иерархии. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] также поддерживают переводы объектов кубов.  
  
 Переводы обеспечивают серверную поддержку клиентских приложений, которые поддерживают несколько языков. Часто пользователи из разных стран просматривают куб и его измерения. Полезно иметь возможность перевода различных элементов куба и его измерений на другой язык, чтобы эти пользователи могли просматривать и понимать куб. Например, если пользователь из Франции обращается к кубу с рабочей станции, имеющей французскую локаль, он видит значения свойства объекта на французском языке. Аналогично пользователь в Германии, обращающийся к тому же кубу с рабочей станции с немецкой локалью, видит те же значения свойства объекта на немецком языке.  
  
 Сведения о параметрах сортировки и языке для компьютера клиента хранятся в виде кода локали. При соединении клиент передает идентификатор языка экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Экземпляр использует этот идентификатор для определения, какой набор переводов необходимо использовать при предоставлении метаданных для объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Если объект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не содержит заданного перевода, то для возвращения содержимого обратно клиенту используется язык по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [Переводы куба](../multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Переводы &#40;служб Analysis Services&#41;](../translations-analysis-services.md)   
 [Советы и рекомендации по глобализации (службы Analysis Services)](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
