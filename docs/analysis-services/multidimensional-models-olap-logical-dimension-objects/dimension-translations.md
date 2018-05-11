---
title: Переводы измерений | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 091cdc3f770297e5fdf231582d5fd2d26d6e8c35
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="dimension-translations"></a>Переводы измерений
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Перевод — это простой механизм для отображения меток и заголовков на другом языке. Каждый перевод определяется как пара значений: строка с переведенным текстом и значение с идентификатором языка. Переводы доступны для всех объектов в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Значения атрибутов измерений также можно перевести. Клиентское приложение отвечает за поиск языка, заданного пользователем, и отображения на этом языке всех меток и заголовков. Объект может иметь неограниченное число переводов.  
  
 Простой объект <xref:Microsoft.AnalysisServices.Translation> содержит кода языка и переведенного заголовка. Номер идентификатора языка **целое** с идентификатором языка. Переведенное текстовое обозначение является заголовком.  
  
 В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], перевод измерений — это зависящее от языка представление имени измерения, имени объекта [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объект или одно из его элементов, например заголовка, элемента или уровня иерархии. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] также поддерживают переводы объектов кубов.  
  
 Переводы обеспечивают серверную поддержку клиентских приложений, которые поддерживают несколько языков. Часто пользователи из разных стран просматривают куб и его измерения. Полезно иметь возможность перевода различных элементов куба и его измерений на другой язык, чтобы эти пользователи могли просматривать и понимать куб. Например, если пользователь из Франции обращается к кубу с рабочей станции, имеющей французскую локаль, он видит значения свойства объекта на французском языке. Аналогично пользователь в Германии, обращающийся к тому же кубу с рабочей станции с немецкой локалью, видит те же значения свойства объекта на немецком языке.  
  
 Сведения о параметрах сортировки и языке для компьютера клиента хранятся в виде кода локали. При соединении клиент передает идентификатор языка экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Экземпляр использует этот идентификатор для определения, какой набор переводов необходимо использовать при предоставлении метаданных для объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Если объект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не содержит заданного перевода, то для возвращения содержимого обратно клиенту используется язык по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [Переводы куба](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Поддержка параметров перевода в службы Analysis Services](../../analysis-services/translation-support-in-analysis-services.md)   
 [Глобализация советы и лучшие методики & #40; Службы Analysis Services & #41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
