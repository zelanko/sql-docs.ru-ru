---
title: Разработка объектов управления аналитикой (AMO) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: amo
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f47c7fe9abc3b7a23c0eea2dd78a536fb9e0ad2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027574"
---
# <a name="developing-with-analysis-management-objects-amo"></a>Разработка объектов управления аналитикой (объекты AMO)
Объекты управления Analysis (AMO) — это полная библиотека доступных программным образом объектов, позволяет приложению управлять запущенным экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].

В этом разделе описываются основные понятия AMO, причем главным образом речь идет об основных объектах, о том, как и когда они используются, а также том, как они взаимосвязаны. Дополнительные сведения об определенных объектов или классов см. в разделе:

- [Пространство имен Microsoft.AnalysisServices](http://msdn.microsoft.com/library/microsoft.analysisservices.aspx), справочную документацию
- [Объекты управления Analysis Services (AMO)](http://www.bing.com/search?q=Analysis+Services+Management+Objects+%28AMO%29), как общие поиска Bing.com.


 **Новые возможности SQL Server 2016**

В SQL Server 2016 AMO рефакторинг и теперь находится в несколько сборок. Универсальные классы, таких как сервера, базы данных и ролей в **Microsoft.AnalysisServices.Core** пространства имен. Интерфейсы API для разных многомерных остаются в [Microsoft.AnalysisServices имен](https://msdn.microsoft.com/library/ms146720.aspx).

Пользовательские сценарии и приложения, написанные для более ранней версии объектов AMO будут продолжать работать без изменения. Тем не менее при наличии сценариев или приложений, ориентированных на SQL Server 2016 специально или необходимо заново осуществить построение пользовательского решения, не забудьте добавить новую сборку и пространство имен в проект.

## <a name="see-also"></a>См. также
[Развертывание с помощью функций анализа служб языка сценариев &#40;ASSL&#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)
[разработки с использованием XML для Аналитики в службах Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)
