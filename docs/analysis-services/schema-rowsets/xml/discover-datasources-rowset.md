---
title: "Набор строк DISCOVER_DATASOURCES | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DISCOVER_DATASOURCES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_DATASOURCES rowset
ms.assetid: f3ff26ab-a447-416b-ba54-1716df2283de
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9c91d5b1d3e0fb7ec972e47079a1bf36d8f9b87
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discoverdatasources-rowset"></a>Набор строк DISCOVER_DATASOURCES
  Возвращает список источников данных поставщика XML для аналитики, которые доступны на сервере или в веб-службе. Для возврата источников опубликованных данных применяется URL-адрес веб-сервера приложения. Клиент может подключиться к одному из источников данных в этом списке.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_DATASOURCES** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover** метод возвращает **DISCOVER_DATASOURCES** набора строк.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Клиент выбирает источник данных, задав **DataSourceInfo** свойство в [свойства](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) элемент, который отправляется вместе с [команда](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md) элемента по [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод. В клиенте не следует создавать содержимое свойства **DataSourceInfo** для отправки на сервер. Вместо этого в клиенте необходимо использовать метод **Discover** для поиска источников данных, поддерживаемых поставщиком. Затем клиент отправляет обратно то же значение для свойства **DataSourceInfo** , которое было им получено из набора строк **DISCOVER_DATASOURCES** .  
  
 Набор строк **DISCOVER_DATASOURCES** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**Источнику данных**|**DBTYPE_WSTR**|Да|Имя источника данных, такое как **Adventure Works**.|  
|**DataSourceDescription**|**DBTYPE_WSTR**||Описание источника данных, введенное издателем.<br /><br /> Может возвращать значение **NULL**.|  
|**URL-адрес**|**DBTYPE_WSTR**|Да|Уникальный путь, который показывает, откуда следует вызывать методы XML для аналитики для этого источника данных.<br /><br /> Может возвращать значение **NULL**.|  
|**DataSourceInfo**|**DBTYPE_WSTR**||Строка, которая содержит любые дополнительные сведения, необходимые для подключения к источнику данных.<br /><br /> Может возвращать значение **NULL**.|  
|**ProviderName**|**DBTYPE_WSTR**|Да|Имя поставщика для источника данных.<br /><br /> Пример:`"MSOLAP"`<br /><br /> Может возвращать значение **NULL**.|  
|**ProviderType**|**DBTYPE_WSTR**|Да|Типы данных, поддерживаемые поставщиком. Этот массив может включать один или несколько следующих типов:<br /><br /> **MDP**. Поставщик многомерных данных.<br /><br /> **TDP**. Поставщик табличных данных.<br /><br /> **DMP**. Поставщик интеллектуального анализа данных (реализовывает технологию OLE для DB применительно к спецификации интеллектуального анализа данных).|  
|**AuthenticationMode**|**DBTYPE_WSTR**|Да|Спецификация, определяющая тип режима безопасности, используемого в источнике данных. Значением может быть одно из следующих.<br /><br /> **Unauthenticated**: Не требуется отправка какого-либо идентификатора пользователя или пароля.<br /><br /> **Authenticated**: Идентификатор пользователя и пароль должны быть включены в сведения, необходимые для подключения к источнику данных.<br /><br /> **Интегрированный**: источник данных используются базовые средства безопасности для определения авторизации, такие как встроенная безопасность, обеспечиваемая [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS).|  
  
 Этот набор строк схемы не отсортирован.  
  
> [!IMPORTANT]  
>  Набор строк **DISCOVER_DATASOURCES** нельзя запрашивать с помощью запросов динамического административного представления и синтаксиса команды SELECT. Тем не менее **DISCOVER_DATASOURCES** набора строк можно запрашивать с помощью <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|06c03d41-f66d-49f3-b1b8-987f7af4cf18|  
|ADOMDNAME|DataSources|  
  
## <a name="see-also"></a>См. также:  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

