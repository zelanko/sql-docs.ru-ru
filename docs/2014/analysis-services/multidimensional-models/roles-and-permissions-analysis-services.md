---
title: Роли и разрешения (службы Analysis Services) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 253cd429c1a5fc5ac231173c88e6ee91b852625a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096268"
---
# <a name="roles-and-permissions-analysis-services"></a>Роли и разрешения (службы Analysis Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] включает ролевую модель авторизации, которая предоставляет доступ к операциям, объектам и данным. Все пользователи получают доступ к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или базе данных в контексте некоторой роли.  
  
 В качестве системного администратора службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , вы отвечаете за предоставление членства **роли администратора сервера** , которая передает неограниченный доступ к операциям на сервере. Эта роль имеет фиксированные разрешения, и ее нельзя настраивать. По умолчанию члены локальной группы администраторов автоматически являются системными администраторами служб Analysis Services.  
  
 Пользователи без прав администратора, которые запрашивают или обрабатывают данные, получают доступ через **роли базы данных**. И системные администраторы и администраторы баз данных могут создавать роли, которые описывают разные уровни доступа в рамках заданной базы данных, а затем назначают членство каждому пользователю, которому необходим доступ. Каждая роль обладает настраиваемым набором разрешений для доступа к объектам и операциям в рамках отдельной базы данных. Разрешения назначаются на уровне базы данных, на уровне внутренних объектов (кубов и измерений, но не перспектив) и на уровне строк.  
  
 Распространенной практикой является разделение операций по созданию ролей и назначению членства. Часто разработчик моделей добавляет роли на этапе проектирования. Таким образом, все определения ролей отражаются в файлах проекта, определяющих модели. Членство в ролях обычно определяется позднее, когда база данных переносится в рабочую среду. Обычно членство назначают администраторы базы данных, которые создают скрипты для разработки, тестирования и выполнения в качестве независимой операции.  
  
 Вся авторизация выполняется по допустимому удостоверению пользователя Windows. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют для проверки подлинности удостоверений пользователей исключительно проверку подлинности Windows. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляет метод проверки подлинности. В разделе [методики проверки подлинности, поддерживаемые службами Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md).  
  
> [!IMPORTANT]  
>  Разрешения являются аддитивными для каждого пользователя или группы Windows, по всем ролям базы данных. Если одна роль запрещает пользователю или группе выполнять определенные задачи или просматривать определенные данные, а другая роль предоставляет такое разрешение указанному пользователю или группе, то этому пользователю или группе будет разрешено выполнять упомянутые задачи или просматривать упомянутые данные.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Предоставление доступа к объектам и операциям &#40;служб Analysis Services&#41;](authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [Предоставление разрешений базы данных &#40;служб Analysis Services&#41;](grant-database-permissions-analysis-services.md)  
  
-   [Предоставление разрешений кубу или модели &#40;служб Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)  
  
-   [Предоставление разрешений на обработку &#40;служб Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
-   [Предоставление разрешений на чтение описания метаданным объекта &#40;служб Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [Предоставление разрешений на объект источника данных &#40;служб Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [Предоставление разрешений на структуры интеллектуального анализа данных и моделей &#40;служб Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [Предоставление разрешений на измерение &#40;служб Analysis Services&#41;](grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [Предоставление настраиваемого доступа к данным измерения &#40;служб Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [Предоставление настраиваемого доступа к данным ячейки &#40;служб Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a>См. также  
 [Создание и управление ролями &#40;табличные службы SSAS&#41;](../tabular-models/roles-ssas-tabular.md)  
  
  