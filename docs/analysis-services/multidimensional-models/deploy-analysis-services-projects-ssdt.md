---
title: "Развертывание проектов служб Analysis Services (SSDT) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8d115e6a40d8954641d0cfc39636748de15636cf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deploy-analysis-services-projects-ssdt"></a>Развертывание проектов служб Analysis Services (среда SSDT)
  В процессе разработки проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]проект часто развертывается на сервере разработки для создания базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , определенной проектом. Это необходимо для тестирования проекта; например для обзора ячеек в кубе, обзора элементов измерения или проверки формул ключевых показателей эффективности.  
  
## <a name="deploying-a-project"></a>Развертывание проекта  
 Проект можно развернуть независимо или же развернуть все проекты в решении. При развертывании проекта последовательно произойдет следующее. Во-первых, будет строиться проект. Этот шаг создает выходные файлы, определяющие базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и ее составляющие объекты. Во-вторых, проверяется целевой сервер. И наконец, на целевом сервере создается целевая база данных и ее объекты. Во время развертывания его механизм полностью заменяет любую существующую базу данных содержимым проекта, если только эти объекты не были созданы проектом во время предыдущего развертывания.  
  
 После первоначального развертывания, создается файл IncrementalSnapshot.xml в \<имя проекта > \obj папки. Этот файл нужен для определения, изменялась ли база данных или ее объекты на целевом сервере вне проекта. Если изменение имело место, система предложит переписать все объекты в целевой базе данных. Если все изменения были сделаны в проекте и проект настроен для добавочного развертывания, на целевом сервере будут развернуты только изменения.  
  
 Конфигурация проекта и соответствующие параметры определяют свойства развертывания, которые будут применяться при развертывании проекта. В общем проекте каждый разработчик использует свою собственную конфигурацию с собственными параметрами конфигурации проекта. Например, каждый разработчик может указать отдельный тестовый сервер для работы отдельно от других разработчиков.  
  
## <a name="see-also"></a>См. также  
 [Создание проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  

