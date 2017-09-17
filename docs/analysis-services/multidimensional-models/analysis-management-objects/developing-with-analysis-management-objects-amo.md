---
title: "Разработка объектов управления аналитикой (AMO) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Management Objects, programming
- AMO, programming
ms.assetid: 91354fc9-22da-4724-b97f-3b1e7b0e69d3
caps.latest.revision: 47
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f746ed6c0ad7dc9c0702282f7a508d44cca7f8be
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

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

