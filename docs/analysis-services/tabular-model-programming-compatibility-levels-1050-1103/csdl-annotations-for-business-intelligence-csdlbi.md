---
title: "Заметки языка CSDL для бизнес-аналитики (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
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
ms.assetid: bf6f372a-bc67-45ea-a771-b2dc5b0527e5
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fcb4818edc09599822670e2e379f89bbf35c6fbb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="csdl-annotations-for-business-intelligence-csdlbi"></a>Заметки языка CSDL для бизнес-аналитики (CSDLBI)

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживает представление определения табличной модели в формате XML, называемое языком определения концептуальной схемы с заметками бизнес-аналитики (CSDLBI). В этом разделе представлены общие сведения о CSDLBI и его использовании в моделях данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="understanding-the-role-of-csdl"></a>Основные сведения о роли языка CSDL  
 Язык концептуальной схемы данных (CSDL) — это язык на основе XML, описывающий сущности, связи и функции. Язык CSDL определен как часть платформы Entity Data Framework. Заметки бизнес-аналитики — это расширение, разработанное для поддержки моделирования данных с помощью [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Несмотря на то что язык CSDL совместим с платформой Entity Data Framework, для построения с его помощью табличной модели или основанного на модели отчета не требуются ни знания модели «сущность-связь», ни какие-либо специальные средства. Модели создаются с помощью клиентских средств, таких как [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], или API, таких как объекты AMO, и развертываются на сервере. Клиенты подключаются к модели с помощью файла определения модели, обычно публикуемого в библиотеке SharePoint, где его могут использовать конструкторы отчетов и пользователи отчетов. Для просмотра дополнительных сведений перейдите по следующим ссылкам:  
  
-   [Решения табличных моделей (табличные службы SSAS)](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md)  
  
-   [Развертывание решений табличной модели (табличные службы SSAS)](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
-   [Соединение семантической модели бизнес-аналитики PowerPivot (BISM-файлы)](../../analysis-services/power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)  
  
 Схема CSDLBI создается сервером служб Analysis Services в ответ на запрос определения модели от клиентских средств, таких как [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. Клиентское приложение отправляет XML-запрос серверу служб Analysis Services, на котором размещены данные модели. В ответ сервер отправляет XML-сообщение, содержащее определение сущностей в модели с использованием заметок CSDLBI. С помощью этих сведений клиентское средство создания отчетов представляет поля, статистические выражения и меры, доступные в модели. Заметки CSDLBI также содержат сведения о том, как группировать, сортировать и форматировать данные.  
  
 Общие сведения о CSDLBI см. в разделе [основные понятия CSDLBI](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md).  
  
### <a name="working-with-csdl"></a>Работа с языком CSDL  
 Набор заметок CSDLBI, представляющий любую конкретную табличную модель, — это XML-документ, содержащий коллекцию сущностей, как простых, так и сложных. Сущности определяют таблицы (или измерения), столбцы (атрибуты), ассоциации (связи) и формулы, включенные в вычисляемые столбцы, меры и ключевые показатели эффективности.  
  
 Эти объекты нельзя изменять непосредственно, для их изменения следует использовать клиентские средства и API-интерфейсы для работы с табличными моделями.  
  
 CSDL-код для модели можно получить, отправив запрос DISCOVER на сервер, на котором размещается модель. Запрос следует уточнить, указав сервер и модель, а также при необходимости представление или перспективу. Возвращаемое сообщение является XML-строкой. Некоторые элементы зависят от языка и могут возвращать разные значения в зависимости от языка текущего соединения. Дополнительные сведения см. в разделе [строк DISCOVER_CSDL_METADATA](../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md).  
  
### <a name="csdlbi-versions"></a>Версии CSDLBI  
 Изначальная спецификация языка CSDL (для платформы Entity Data Framework) предоставляет большинство сущностей и свойств, необходимых для моделирования. Заметки бизнес-аналитики поддерживают особые требования табличных моделей, необходимые для клиентов (таких как [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]) свойства отчетов и дополнительные метаданные, необходимые для многомерных моделей. В этом разделе описаны изменения в каждой версии.  
  
 **CSDLBI 1.0**  
  
 Начальный набор добавлений в схему CSDL для поддержки табличных моделей [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] содержал заметки для поддержки моделирования данных, пользовательских вычислений и расширенного представления.  
  
-   Новые элементы и свойства для поддержки табличных моделей. Например, было добавлено свойство для указания типа запроса к базе данных, используемого для заполнения модели.  
  
-   Новые свойства и расширения существующих сущностей.  Например, элемент Association был расширен для поддержки связей.  
  
-   Свойства визуализации и навигации. Например, добавлены свойства для поддержки пользовательских полей сортировки, изображений по умолчанию и  
  
 **CSDLBI 1.1**  
  
 Эта версия схемы CSDLBI включает расширения для поддержки многомерных баз данных (таких как кубы OLAP). Новые элементы и свойства имеют следующий вид:  
  
-   Поддержка измерений как сущностей.  
  
-   Поддержка иерархий.  
  
-   Доступ к разделам ROLAP.  
  
-   Поддержка переводов.  
  
-   Поддержка перспектив.  
  
 Подробные сведения об отдельных элементах в заметки CSDLBI см [Технический справочник по заметки бизнес-Аналитики для языка CSDL](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md). Сведения о базовой спецификации языка CSDL см. в разделе [спецификация языка CSDL](http://go.microsoft.com/fwlink/?LinkId=205855) на сайте MSDN.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Основные понятия CSDLBI](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)   
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
