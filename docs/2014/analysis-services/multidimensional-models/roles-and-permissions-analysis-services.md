---
title: Роли и разрешения (Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f536ae91cde1301b9499b2d36957d25c877be9c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66073062"
---
# <a name="roles-and-permissions-analysis-services"></a>Роли и разрешения (службы Analysis Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]предоставляет модель авторизации на основе ролей, которая предоставляет доступ к операциям, объектам и данным. Все пользователи получают доступ к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или базе данных в контексте некоторой роли.  
  
 В качестве системного администратора службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , вы отвечаете за предоставление членства **роли администратора сервера** , которая передает неограниченный доступ к операциям на сервере. Эта роль имеет фиксированные разрешения, и ее нельзя настраивать. По умолчанию члены локальной группы администраторов автоматически являются системными администраторами служб Analysis Services.  
  
 Пользователи без прав администратора, которые запрашивают или обрабатывают данные, получают доступ через **роли базы данных**. И системные администраторы и администраторы баз данных могут создавать роли, которые описывают разные уровни доступа в рамках заданной базы данных, а затем назначают членство каждому пользователю, которому необходим доступ. Каждая роль обладает настраиваемым набором разрешений для доступа к объектам и операциям в рамках отдельной базы данных. Разрешения назначаются на уровне базы данных, на уровне внутренних объектов (кубов и измерений, но не перспектив) и на уровне строк.  
  
 Распространенной практикой является разделение операций по созданию ролей и назначению членства. Часто разработчик моделей добавляет роли на этапе проектирования. Таким образом, все определения ролей отражаются в файлах проекта, определяющих модели. Членство в ролях обычно определяется позднее, когда база данных переносится в рабочую среду. Обычно членство назначают администраторы базы данных, которые создают скрипты для разработки, тестирования и выполнения в качестве независимой операции.  
  
 Вся авторизация выполняется по допустимому удостоверению пользователя Windows. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]использует проверку подлинности Windows исключительно для проверки подлинности удостоверений пользователей. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]не предоставляет собственный метод проверки подлинности. См. статью [методологии проверки подлинности, поддерживаемые Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md).  
  
> [!IMPORTANT]  
>  Разрешения являются аддитивными для каждого пользователя или группы Windows, по всем ролям базы данных. Если одна роль запрещает пользователю или группе выполнять определенные задачи или просматривать определенные данные, а другая роль предоставляет такое разрешение указанному пользователю или группе, то этому пользователю или группе будет разрешено выполнять упомянутые задачи или просматривать упомянутые данные.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Авторизация доступа к объектам и операциям &#40;Analysis Services&#41;](authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [Grant, предоставление разрешений на базу данных &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)  
  
-   [Предоставление разрешений куба или модели &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)  
  
-   [Предоставление разрешений на обработку &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
-   [Предоставьте разрешения на чтение описания для метаданных объекта &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [Предоставление разрешений на объект источника данных &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [Предоставление разрешений на структуры и модели интеллектуального анализа данных &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [Предоставление разрешений на Analysis Services &#40;измерения&#41;](grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [Предоставление настраиваемого доступа к данным измерения &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [Предоставление настраиваемого доступа к данным ячейки &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание ролей и управление ими &#40;табличных&#41;SSAS](../tabular-models/roles-ssas-tabular.md)  
  
  
