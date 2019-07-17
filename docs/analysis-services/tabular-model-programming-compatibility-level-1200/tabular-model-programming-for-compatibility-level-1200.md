---
title: Analysis Services табличной модели программирования для уровня совместимости 1200 | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7493c09964db2e0a8cbd17c6a2278dd554a2dcc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207888"
---
# <a name="tabular-model-programming-for-compatibility-level-1200-and-higher"></a>Программирование табличных моделей с уровнем совместимости 1200 и выше
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Начиная с уровнем совместимости 1200 табличных метаданных используется для описания модели конструкции, заменив исторических многомерные метаданные как дескрипторы для табличной модели объектов. Метаданные для таблицы, столбцы и связи являются таблицы, столбца и связи, а не многомерные аналоги (измерений и атрибутов).  
  
Можно создать новые модели на уровне совместимости 1200 или выше с помощью API Microsoft.AnalysisServices.Tabular, последнюю версию из SQL Server Data Tools (SSDT), или путем изменения **CompatibilityLevel** существующих табличных модель, чтобы обновить его (также выполняется в SSDT). Это привязывает модель к более новым версиям сервера, средств и программных интерфейсов.   
  
Обновление существующего табличного решения рекомендуется, но не является обязательным. Существующий скрипт и пользовательских решений, которые используют или управление табличными моделями или баз данных можно использовать в качестве-является. Более низких уровнях совместимости, полностью поддерживаются в SQL Server 2016 с помощью функции, доступные на этом уровне. Службы Azure Analysis Services поддерживает только уровень совместимости 1200 и выше.
  
 Новых табличных моделей требуется различный код и скрипт, представлены ниже.  
  
## <a name="object-model-definitions-as-tabular-metadata-constructs"></a>Определения модели объектов как конструкции табличных метаданных  
 Табличная модель объектов для моделей 1200 или выше предоставляется в JSON с помощью [Tabular Model Scripting Language](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference) и с помощью языка описания данных AMO через новое пространство имен, [ Microsoft.AnalysisServices.Tabular](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.aspx)

## <a name="script-for-tabular-models-and-databases"></a>Скрипт для табличных моделей и баз данных  
 TMSL — это JSON язык сценариев для табличных моделей с поддержкой для создания, чтения, обновления, операции удаления. Можно обновить данные через TMSL и вызова операций базы данных для присоединения, отъединение, резервное копирование, восстановление и синхронизация.  
  
 Объекты AMO PowerShell в качестве входных данных принимает скрипт TMSL.  
  
 См. в разделе [Tabular Model Scripting Language &#40;TMSL&#41; ссылку](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference) и [Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md) Дополнительные сведения.  
  
## <a name="query-languages"></a>Языки запросов  
 DAX и многомерных Выражений поддерживаются для всех табличных моделей.  
  
## <a name="expression-language"></a>Язык выражений  
 Фильтры и выражения, используемые для создания вычисляемых объектов, включая меры и ключевые показатели эффективности, организуются в DAX. См. в разделе [основные сведения о DAX в табличных моделях](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md) и [выражения анализа данных &#40;DAX&#41; в службах Analysis Services](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5).  
  
## <a name="managed-code-for-tabular-models-and-databases"></a>Управляемый код для табличных моделей и баз данных  
 Объекты AMO включают новое пространство имен Microsoft.AnalysisServices.Tabular, для работы с моделями, программными средствами. См. в разделе [пространства имен Microsoft.AnalysisServices](https://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx) Дополнительные сведения.  
  
> [!NOTE]  
>  Клиентские библиотеки объекты управления Analysis Services (AMO), ADOMD.NET и табличной модели объектов (TOM) теперь Выбор среды выполнения .NET 4.0.   
  
## <a name="see-also"></a>См. также  
 [Документация для разработчика служб Analysis Services](../../analysis-services/analysis-services-developer-documentation.md)   
 [Программирование табличных моделей для совместимости уровни 1050 по 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)   
 [Технический справочник по](../../analysis-services/powershell/technical-reference-ssas.md)[обновление служб Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)  
 [Уровень совместимости табличных моделей и баз данных](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)  
  
  
