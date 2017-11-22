---
title: "Расширение функциональных возможностей OLAP | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c7ba26b786b4f7cd99970bc9f5254dbac5da4f1f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="extending-olap-functionality"></a>Расширение функциональных возможностей OLAP
  Программист может расширять службы Analysis Services, написав сборки, персонализированные расширения и хранимые процедуры, обеспечивающие нужные функциональные возможности, которые можно использовать один или несколько раз в разнообразных приложениях базы данных. Сборки используются для расширения функциональных возможностей многомерных моделей путем добавления новых процедур и функций в язык многомерных выражений или путем встраивания персонализации.  
  
 Хранимые процедуры могут использоваться для вызова внешних подпрограмм, упрощая разработку и внедрение баз данных служб Analysis Services за счет однократной разработки общего программного кода и сохранения его в единственном местоположении. Хранимые процедуры можно использовать для расширения функциональности приложений за счет добавления дополнительных функций к собственной функциональности многомерных выражений.  
  
 Персонализации представляют собой пользовательские объекты, которые могут добавляться в куб для обеспечения функций, которые отличаются от пользователя к пользователю. Персонализации не являются постоянными объектами куба, но представляют собой объекты, которые динамически применяются клиентским приложением во время сеанса конкретного пользователя. Например, изменение валют в денежном выражении в зависимости от пользователя, который осуществляет доступ к данным, предоставление индивидуальных ключевых показателей эффективности или целевых списков предложений для постоянных покупателей в сети.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Расширение OLAP через личные настройки](../../../analysis-services/multidimensional-models/extending-olap/extending-olap-through-personalizations.md)  
  
 [Расширения персонализации служб Analysis Services](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
 [Определение хранимых процедур](../../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
