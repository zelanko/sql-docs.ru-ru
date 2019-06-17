---
title: Переводы куба | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- cubes [Analysis Services], translations
- OLAP objects [Analysis Services], translations
- translations [Analysis Services], cubes
ms.assetid: 4e4fd6a4-d324-4508-b75a-2a57de9ab8ff
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c34024f61f5c7b42030e0acb848783e1acae3d6e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62728510"
---
# <a name="cube-translations"></a>Переводы куба
  Перевод — это простой механизм для отображения меток и заголовков на другом языке. Каждый перевод определяется как пара значений: строка с переведенным текстом и значение с идентификатором языка. Переводы доступны для всех объектов в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Значения атрибутов измерений также можно перевести. Клиентское приложение отвечает за поиск языка, заданного пользователем, и отображения на этом языке всех меток и заголовков. Объект может иметь неограниченное число переводов.  
  
 Простой объект <xref:Microsoft.AnalysisServices.Translation> содержит кода языка и переведенного заголовка. Код языка — это значение типа `Integer` с идентификатором языка. Переведенное текстовое обозначение является заголовком.  
  
 В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Переводы куба представляют зависящие от языка представление имени объекта куба, например заголовка или папки отображения. Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] также поддерживают переводы имен измерений и элементов.  
  
 Переводы обеспечивают серверную поддержку клиентских приложений, которые поддерживают несколько языков. Часто данные куба просматривают пользователи из разных стран. Полезно иметь возможность переводить различные элементы куба на другой язык, чтобы пользователи в разных странах могли просматривать и понимать метаданные куба. Например, если пользователь из Франции обращается к кубу с рабочей станции, имеющей французскую локаль, он видит значения свойств объекта на французском языке. Аналогично пользователь в Германии может обращаться к тому же кубу с рабочей станции с немецкой локалью и просматривать значения свойств объекта на немецком языке.  
  
 Сведения о параметрах сортировки и языке для компьютера клиента хранятся в виде кода локали. При соединении клиент передает идентификатор языка экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Экземпляр использует этот код языка, чтобы определить, какой набор переводов необходимо использовать при предоставлении метаданных для объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для каждого пользователя. Если объект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не содержит заданного перевода, то для возвращения содержимого обратно клиенту используется язык по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [Переводы измерений](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Переводы &#40;служб Analysis Services&#41;](../translations-analysis-services.md)   
 [Советы и рекомендации по глобализации (службы Analysis Services)](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
