---
title: Введение в классы объектов AMO | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Management Objects]
- classes [AMO]
ms.assetid: d3c066bc-f812-4d53-9e96-9e306f2fc580
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eb4e3761642f8b03e5853ae99e00cc4bc2f4a46f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328534"
---
# <a name="introducing-amo-classes"></a>Знакомство с классами объектов AMO
  Объекты AMO — это библиотека классов, предназначенных для управления экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] из клиентского приложения. Классы AMO — это классы, которые используются для администрирования таких объектов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , как базы данных, измерения, кубы, структуры и модели интеллектуального анализа, роли и разрешения, исключения и др.  
  
 На следующем рисунке показана связь между классами, описываемыми в этом разделе.  
  
 ![Классы, описываемые в концептуальных разделов AMO](../../../analysis-services/dev-guide/media/amo-reviewedclasses.gif "классы, описываемые в концептуальных разделов объектов AMO")  
  
 Библиотеку объектов AMO можно описать как логически связанные группы объектов, используемых для выполнения определенной задачи. Классы AMO можно категоризировать следующим образом. В этом разделе рассматриваются следующие вопросы.  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Основные классы объектов AMO](amo-fundamental-classes.md)|Описывает классы, необходимые для работы с любым другим набором классов.|  
|[Классы OLAP объектов AMO](amo-olap-classes.md)|Описывает классы, позволяющие управлять объектами OLAP в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Классы интеллектуального анализа данных объектов AMO](amo-data-mining-classes.md)|Описывает классы, позволяющие управлять объектами интеллектуального анализа данных в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Классы безопасности объектов AMO](amo-security-classes.md)|Описывает классы, позволяющие управлять доступом к другим объектам и обеспечивать безопасность.|  
|[Другие классы и методы объектов AMO](amo-other-classes-and-methods.md)|Описывает классы и методы, помогающие администраторам OLAP и интеллектуального анализа данных выполнять свои повседневные задачи.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices>   
 [Логическая архитектура &#40;службы Analysis Services — многомерные данные&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Объекты базы данных &#40;службы Analysis Services — многомерные данные&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [Разработка объектов управления аналитикой &#40;объектов AMO&#41;](developing-with-analysis-management-objects-amo.md)  
  
  
