---
title: "Переводы куба | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- cubes [Analysis Services], translations
- OLAP objects [Analysis Services], translations
- translations [Analysis Services], cubes
ms.assetid: 4e4fd6a4-d324-4508-b75a-2a57de9ab8ff
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 65ba720400e5549bfe640297269f4d00afe5c988
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="cube-translations"></a>Переводы куба
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Перевод — это простой механизм для изменения отображения меток и заголовков с одного языка на другой. Каждый перевод определяется как пара значений: строка с переведенным текстом и значение с идентификатором языка. Переводы доступны для всех объектов в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Значения атрибутов измерений также можно перевести. Клиентское приложение отвечает за поиск языка, заданного пользователем, и отображения на этом языке всех меток и заголовков. Объект может иметь неограниченное число переводов.  
  
 Простой объект <xref:Microsoft.AnalysisServices.Translation> содержит кода языка и переведенного заголовка. Номер идентификатора языка **целое** с идентификатором языка. Переведенное текстовое обозначение является заголовком.  
  
 В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Переводы куба представляют зависящее от языка представление имени объекта куба, например заголовка или папки отображения. Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] также поддерживают переводы имен измерений и элементов.  
  
 Переводы обеспечивают серверную поддержку клиентских приложений, которые поддерживают несколько языков. Часто данные куба просматривают пользователи из разных стран. Полезно иметь возможность переводить различные элементы куба на другой язык, чтобы пользователи в разных странах могли просматривать и понимать метаданные куба. Например, если пользователь из Франции обращается к кубу с рабочей станции, имеющей французскую локаль, он видит значения свойств объекта на французском языке. Аналогично пользователь в Германии может обращаться к тому же кубу с рабочей станции с немецкой локалью и просматривать значения свойств объекта на немецком языке.  
  
 Сведения о параметрах сортировки и языке для компьютера клиента хранятся в виде кода локали. При соединении клиент передает идентификатор языка экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Экземпляр использует этот код языка, чтобы определить, какой набор переводов необходимо использовать при предоставлении метаданных для объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для каждого пользователя. Если объект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не содержит заданного перевода, то для возвращения содержимого обратно клиенту используется язык по умолчанию.  
  
## <a name="see-also"></a>См. также:  
 [Переводы измерений](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Поддержка параметров перевода в службы Analysis Services](../../analysis-services/translation-support-in-analysis-services.md)   
 [Глобализация советы и лучшие методики &#40; Службы Analysis Services &#41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
