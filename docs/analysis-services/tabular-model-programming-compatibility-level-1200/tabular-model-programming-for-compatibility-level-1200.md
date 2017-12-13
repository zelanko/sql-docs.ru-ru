---
title: "Программирование табличных моделей уровня совместимости 1200 | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d343f693-c800-42fe-bb4f-2c38a10919f1
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 5c7a0c3c69a8d4c834cf6a44cd3e588faed2593f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="tabular-model-programming-for-compatibility-level-1200-and-higher"></a>Табличные модели программирования для совместимости уровня 1200 и выше
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Начиная с уровнем совместимости 1200, табличных метаданных используется для описания модели конструкций, заменив исторических многомерные метаданные как дескрипторы для табличной модели объектов. Метаданные для таблицы, столбцы и связи являются таблицы, столбца и связи, а не многомерные эквиваленты (измерений и атрибутов).  
  
Можно создавать новые модели на уровне совместимости 1200 или выше с помощью API Microsoft.AnalysisServices.Tabular, последнюю версию из SQL Server Data Tools (SSDT), или путем изменения **CompatibilityLevel** существующих табличных модель для обновления (также выполняется в SSDT). Таким образом привязывает модель к более новым версиям сервера, средств и программных интерфейсов.   
  
Обновление существующего табличного решения рекомендуется, но не является обязательным. Существующий скрипт и пользовательских решений, которые используют или управление табличными моделями или баз данных можно использовать в качестве-является. Более ранними уровнями совместимости полностью поддерживаются в SQL Server 2016 с помощью функции, доступные на этом уровне. Azure Analysis Services поддерживает только уровень совместимости 1200 и выше.
  
 Новых табличных моделей потребуется другой код и сценарии, в приведенных ниже разделах.  
  
## <a name="object-model-definitions-as-tabular-metadata-constructs"></a>Определения модели объектов как конструкции табличных метаданных  
 Объектную модель табличных моделей 1200 или выше представлены в JSON через [языке скриптов табличных моделей](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) и с помощью языка описания данных объектов AMO через новое пространство имен [ Microsoft.AnalysisServices.Tabular](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.aspx)

## <a name="script-for-tabular-models-and-databases"></a>Скрипт для табличных моделей и баз данных  
 TMSL — это JSON язык сценариев для табличных моделей с поддержкой создание, чтение, обновление, операции удаления. Можно обновить данные через TMSL и вызова операций базы данных для присоединения, отъединение, резервного копирования и восстановления и синхронизации.  
  
 Объекты AMO PowerShell сценарий TMSL принимает в качестве входных данных.  
  
 В разделе [табличной модели, сценарии языка &#40; TMSL &#41; Справочник по](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) и [Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md) для получения дополнительной информации.  
  
## <a name="query-languages"></a>Языки запросов  
 DAX и многомерных Выражений поддерживаются для всех табличных моделей.  
  
## <a name="expression-language"></a>Язык выражений  
 Фильтры и выражения, используемые для создания вычисляемых объектов, включая меры и ключевые показатели эффективности, организуются в DAX. В разделе [основные сведения о DAX в табличных моделях](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md) и [выражения анализа данных &#40; DAX &#41; в службах Analysis Services](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5).  
  
## <a name="managed-code-for-tabular-models-and-databases"></a>Управляемый код для табличных моделей и баз данных  
 Объекты AMO включает новое пространство имен Microsoft.AnalysisServices.Tabular, для работы с моделями, программными средствами. В разделе [Microsoft.AnalysisServices имен](https://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx) для получения дополнительной информации.  
  
> [!NOTE]  
>  Клиентские библиотеки табличной модели объектов (TOM), ADOMD.NET и объекты управления Analysis Services (AMO) теперь модуля выполнения .NET 4.0.   
  
## <a name="see-also"></a>См. также:  
 [Документация для разработчика служб Analysis Services](../../analysis-services/analysis-services-developer-documentation.md)   
 [Программирование табличных моделей для обеспечения совместимости уровни 1050 до 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)   
 [Технический справочник по &#40; Службы SSAS &#41; ](../../analysis-services/powershell/technical-reference-ssas.md) [Обновление служб Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)  
 [Уровни совместимости табличных моделей и баз данных](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)  
  
  
