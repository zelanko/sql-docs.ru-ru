---
title: Настройка свойств мер | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e579d8090300e205e99807f8016be066f557b6fb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022231"
---
# <a name="configure-measure-properties"></a>Настройка свойств мер
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Меры имеют свойства, позволяющие определять и управлять их работой и отображением для пользователей.  
  
 Свойства в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] можно задать при создании или изменении куба или меры. Можно также задать их программным способом с помощью многомерных выражений или объектов AMO. Дополнительные сведения см. в разделах [Создание мер и групп мер в многомерных моделях](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md), [Инструкция CREATE MEMBER (многомерные выражения)](../../mdx/mdx-data-definition-create-member.md) и [Программирование основных объектов AMO OLAP](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-basic-objects.md).  
  
## <a name="measure-properties"></a>Свойства мер  
 Меры наследуют определенные свойства у группы мер, элементами которых они являются, если только эти свойства не переопределены на уровне мер. Свойства мер определяют статистическое вычисление, тип данных, отображаемые для пользователей имена, папку отображения, строку форматирования, выражения меры, базовые исходные столбцы и видимость для пользователей.  
  
|Свойство|Определение|  
|--------------|----------------|  
|**AggregateFunction**|Обязательный. Определяет, как выполняется статистическое вычисление мер. **Sum** — это агрегирование по умолчанию. Описание каждой функции см. в разделе [Use Aggregate Functions](../../analysis-services/multidimensional-models/use-aggregate-functions.md) .|  
|**Тип данных**|Обязательный. Указывает тип данных столбца базовой таблицы фактов, к которым привязана мера. Это значение наследуется из исходного столбца по умолчанию.|  
|**Description**|Содержит описание меры, которое может быть видно в клиентских приложениях.|  
|**DisplayFolder**|Указывает папку отображения, в которой будет представлена мера при подключении пользователя к кубу. Если куб содержит множество мер, папки отображения позволяют разбить их по категориям мер, упростив доступ к ним.|  
|**FormatString**|Можно выбрать формат, используемый для отображения значений меры пользователям, используя свойство **FormatString** меры.<br /><br /> Список форматов отображения представлен в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], но можно указать множество дополнительных форматов, не содержащихся в этом списке. Можно указать любой именованный или определенный пользователем формат, допустимый в языке Microsoft Visual Basic.|  
|**Идентификатор**|Обязательный. Отображает уникальный идентификатор (ID) меры. Это свойство предназначено только для чтения.|  
|**MeasureExpression**|Указывает ограниченное многомерное выражение, определяющее значение меры. Выражение вычисляется на конечном уровне до агрегирования и позволяет получить взвешенное значение. Например, конвертация валют, где объем продаж взвешен с учетом обменного курса.|  
|**Название**|Обязательный. Имя меры.|  
|**Source**|Обязательный. Столбец в представлении источника данных, к которому привязана мера. См. раздел [Источники данных и привязки (многомерные службы SSAS)](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).|  
|**Visible**|Определяет видимость меры в клиентских приложениях.|  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств группы мер](../../analysis-services/multidimensional-models/configure-measure-group-properties.md)   
 [Изменение мер](../../analysis-services/lesson-3-1-modifying-measures.md)  
  
  
