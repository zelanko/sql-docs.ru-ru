---
title: Развертывание проектов Analysis Services (SSDT) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5b6c79c2ea4355e9d889e235c8185a2460c0ed8c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075391"
---
# <a name="deploy-analysis-services-projects-ssdt"></a>Развертывание проектов служб Analysis Services (среда SSDT)
  В процессе разработки проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]проект часто развертывается на сервере разработки для создания базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , определенной проектом. Это необходимо для тестирования проекта; например для обзора ячеек в кубе, обзора элементов измерения или проверки формул ключевых показателей эффективности.  
  
## <a name="deploying-a-project"></a>Развертывание проекта  
 Проект можно развернуть независимо или же развернуть все проекты в решении. При развертывании проекта последовательно произойдет следующее. Во-первых, будет строиться проект. Этот шаг создает выходные файлы, определяющие базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и ее составляющие объекты. Во-вторых, проверяется целевой сервер. И наконец, на целевом сервере создается целевая база данных и ее объекты. Во время развертывания его механизм полностью заменяет любую существующую базу данных содержимым проекта, если только эти объекты не были созданы проектом во время предыдущего развертывания.  
  
 После первоначального развертывания в папке \<Project Name> \обж создается файл IncrementalSnapshot. XML. Этот файл нужен для определения, изменялась ли база данных или ее объекты на целевом сервере вне проекта. Если изменение имело место, система предложит переписать все объекты в целевой базе данных. Если все изменения были сделаны в проекте и проект настроен для добавочного развертывания, на целевом сервере будут развернуты только изменения.  
  
 Конфигурация проекта и соответствующие параметры определяют свойства развертывания, которые будут применяться при развертывании проекта. В общем проекте каждый разработчик использует свою собственную конфигурацию с собственными параметрами конфигурации проекта. Например, каждый разработчик может указать отдельный тестовый сервер для работы отдельно от других разработчиков.  
  
## <a name="see-also"></a>См. также:  
 [Создание проекта Analysis Services &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md)  
  
  
