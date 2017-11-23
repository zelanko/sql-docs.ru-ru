---
title: "Разработка объектов управления аналитикой (AMO) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- Analysis Management Objects, programming
- AMO, programming
ms.assetid: 91354fc9-22da-4724-b97f-3b1e7b0e69d3
caps.latest.revision: "47"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bbcf54edc79a1e8254ad6210d327f4a83973f1fd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="developing-with-analysis-management-objects-amo"></a>Разработка объектов управления аналитикой (объекты AMO)
Объекты управления Analysis (AMO) — это полная библиотека доступных программным образом объектов, позволяет приложению управлять запущенным экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].

В этом разделе описываются основные понятия AMO, причем главным образом речь идет об основных объектах, о том, как и когда они используются, а также том, как они взаимосвязаны. Дополнительные сведения об определенных объектов или классов см. в разделе:

- [Пространство имен Microsoft.AnalysisServices](http://msdn.microsoft.com/library/microsoft.analysisservices.aspx), справочную документацию
- [Объекты управления Analysis Services (AMO)](http://www.bing.com/search?q=Analysis+Services+Management+Objects+%28AMO%29), как общие поиска Bing.com.


 **Новые возможности SQL Server 2016**

В SQL Server 2016 AMO рефакторинг и теперь находится в несколько сборок. Универсальные классы, таких как сервера, базы данных и ролей в **Microsoft.AnalysisServices.Core** пространства имен. Интерфейсы API для разных многомерных остаются в [Microsoft.AnalysisServices имен](https://msdn.microsoft.com/library/ms146720.aspx).

Пользовательские сценарии и приложения, написанные для более ранней версии объектов AMO будут продолжать работать без изменения. Тем не менее при наличии сценариев или приложений, ориентированных на SQL Server 2016 специально или необходимо заново осуществить построение пользовательского решения, не забудьте добавить новую сборку и пространство имен в проект.

## <a name="see-also"></a>См. также:
[Разработка с использованием служб Analysis Services Scripting Language &#40; ASSL &#41; ](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) 
 [Разработки с использованием XML для Аналитики в службах Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)
