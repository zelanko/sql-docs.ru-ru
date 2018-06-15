---
title: Классы интеллектуального анализа данных объектов AMO | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: amo
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 803e6738fc526f68b8937efaa2b65be1b7d30dc4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34021601"
---
# <a name="amo-data-mining-classes"></a>Классы интеллектуального анализа данных объектов AMO
  Классы интеллектуального анализа данных позволяют создавать, изменять, удалять и обрабатывать объекты интеллектуального анализа данных. Среди действий при работе с объектами интеллектуального анализа данных — создание структур интеллектуального анализа данных, создание моделей интеллектуального анализа и их обработка.  
  
 Дополнительные сведения о том, как настроить среду, а также об <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, и <xref:Microsoft.AnalysisServices.DataSourceView> объектов, в разделе [основные классы объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md).  
  
 Для определения объектов в объектах AMO требуется задать несколько свойств для каждого объекта, чтобы создать правильный контекст. Сложные объекты, например объекты OLAP и объекты интеллектуального анализа данных, требуют написания длинного и подробного кода.  
  
 Этот раздел состоит из следующих подразделов.  
  
-   [Объекты MiningStructure](#MiningStructure)  
  
-   [Объекты MiningModel](#MiningModel)  
  
 На следующем рисунке показана связь между классами, описываемыми в этом разделе.  
  
 ![Классы AMO для интеллектуального анализа данных](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-dataminingclasses.gif "классы объектов AMO для интеллектуального анализа данных")  
  
##  <a name="MiningStructure"></a> Объекты MiningStructure  
 Структура интеллектуального анализа данных является контейнером для моделей интеллектуального анализа данных. Структура определяет все возможные столбцы, которые могут использоваться в модели интеллектуального анализа данных. В каждой модели интеллектуального анализа данных определяются собственные столбцы из набора столбцов, определенных в структуре.  
  
 Простой объект <xref:Microsoft.AnalysisServices.MiningStructure> состоит из следующих компонентов: базовые сведения, представление источника данных, один или несколько объектов <<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>, от нуля или более объектов <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> и объект <xref:Microsoft.AnalysisServices.MiningModelCollection>.  
  
 Базовые сведения содержат имя и идентификатор (внутренний) объекта <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
 Объект <xref:Microsoft.AnalysisServices.DataSourceView> содержит базовую модель данных для структуры интеллектуального анализа данных.  
  
 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> — это столбцы или атрибуты, имеющие одно значение.  
  
 <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> — это столбцы или атрибуты, имеющие несколько значений для каждого варианта.  
  
 Объект <xref:Microsoft.AnalysisServices.MiningModelCollection> содержит все модели интеллектуального анализа данных, построенные на одних и тех же данных.  
  
 Объект <xref:Microsoft.AnalysisServices.MiningStructure> создается путем добавления его в коллекцию <xref:Microsoft.AnalysisServices.MiningStructureCollection> базы данных и обновления объекта <xref:Microsoft.AnalysisServices.MiningStructure> до сервера при помощи метода Update.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.MiningStructure>, к нему необходимо применить метод Drop объекта <xref:Microsoft.AnalysisServices.MiningStructure>. Удаление объекта <xref:Microsoft.AnalysisServices.MiningStructure> из коллекции не оказывает влияния на сервер.  
  
 Объект <xref:Microsoft.AnalysisServices.MiningStructure> может обрабатываться при помощи собственного метода обработки или обрабатываться тогда, когда родительский объект обрабатывает себя с помощью собственного метода обработки.  
  
### <a name="columns"></a>Столбцы  
 Столбцы содержат данные для модели и могут быть разных типов в зависимости от использования: ключ, входных данных, прогнозируемый или InputPredictable. Прогнозируемые столбцы являются целью построения модели интеллектуального анализа данных.  
  
 В объектах AMO столбцы с одним значением называются <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>. Столбцы с несколькими значениями называются <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
#### <a name="scalarminingstructurecolumn"></a>ScalarMiningStructureColumn  
 Простой объект <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> состоит из базовых сведений, типа, содержимого и привязки данных.  
  
 В общие сведения входит имя и идентификатор (внутренний) столбца <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
 Тип является типом данных значения: LONG, DOUBLE логическое значение, текст, дата.  
  
 Содержимое указывает ядру, как можно моделировать столбец. Значения могут быть: дискретные, непрерывные, дискретизированные, упорядоченный, Cyclical, вероятности, дисперсии, StdDev, ProbabilityVariance, ProbabilityStdDev, поддержка, ключ.  
  
 Привязка данных — это связывание столбца интеллектуального анализа данных с базовой моделью данных при помощи элемента представления источников данных.  
  
 Объект <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> создается путем добавления его в родительский объект <xref:Microsoft.AnalysisServices.MiningStructureCollection> и обновления родительского объекта <xref:Microsoft.AnalysisServices.MiningStructure> до сервера при помощи метода Update.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>, его следует удалить из коллекции родительского объекта <xref:Microsoft.AnalysisServices.MiningStructure>, а сам родительский объект <xref:Microsoft.AnalysisServices.MiningStructure> необходимо обновить до сервера при помощи метода Update.  
  
#### <a name="tableminingstructurecolumn"></a>TableMiningStructureColumn  
 Простой объект <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> состоит из базовых сведений и скалярных столбцов.  
  
 В общие сведения входит имя и идентификатор (внутренний) столбца <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
 Скалярные столбцы представляют собой <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
 Объект <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> создается путем добавления его в родительскую коллекцию <xref:Microsoft.AnalysisServices.MiningStructure> и обновления родительского объекта <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> до сервера при помощи метода Update.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>, его следует удалить из коллекции родительского объекта <xref:Microsoft.AnalysisServices.MiningStructure>, а сам родительский объект <xref:Microsoft.AnalysisServices.MiningStructure> необходимо обновить до сервера при помощи метода Update.  
  
##  <a name="MiningModel"></a> Объекты MiningModel  
 <xref:Microsoft.AnalysisServices.MiningModel> — это объект, позволяющий выбирать для использования столбцы из структуры, алгоритмы, а также дополнительные определенные параметры для настройки модели. Например, может потребоваться определить несколько моделей интеллектуального анализа в одной структуре интеллектуального анализа, которые будут использовать одинаковые алгоритмы, но при этом в одной модели необходимо пропустить некоторые столбцы из структуры интеллектуального анализа, использовать их в качестве входных данных в другой модели, а также использовать их в качестве входных данных и прогноза в третьей. Это полезно в случае, если в одной модели интеллектуального анализа требуется рассматривать столбцы как непрерывные, а в другой — как дискретизированные.  
  
 Простой объект <xref:Microsoft.AnalysisServices.MiningModel> состоит из базовых сведений, определений алгоритма и столбцов.  
  
 Базовые сведения содержат имя и идентификатор (внутренний) модели интеллектуального анализа.  
  
 Под определением алгоритма понимается один из стандартных алгоритмов, представленных в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], или любые пользовательские алгоритмы, включенные на сервере.  
  
 Столбцы — это коллекции столбцов, используемых алгоритмом, и определение их использования.  
  
 Объект <xref:Microsoft.AnalysisServices.MiningModel> создается путем добавления его в коллекцию <xref:Microsoft.AnalysisServices.MiningModelCollection> базы данных и обновления объекта <xref:Microsoft.AnalysisServices.MiningModel> до сервера при помощи метода Update.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.MiningModel>, к нему необходимо применить метод Drop объекта <xref:Microsoft.AnalysisServices.MiningModel>. Удаление объекта <xref:Microsoft.AnalysisServices.MiningModel> из коллекции не влияет на сервер.  
  
 После создания объект <xref:Microsoft.AnalysisServices.MiningModel> может обрабатываться при помощи собственного метода обработки или обрабатываться тогда, когда родительский объект обрабатывает себя с помощью собственного метода обработки.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices>   
 [Основные классы объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)   
 [Программирование объектов интеллектуального анализа данных AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-data-mining-objects.md)   
 [Знакомство с классами объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Логическая архитектура & #40; Analysis Services — многомерные данные & #41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Объекты базы данных & #40; Analysis Services — многомерные данные & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
