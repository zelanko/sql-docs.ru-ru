---
title: Тип данных DataSource (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSource Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSource data type
ms.assetid: 05e8de8d-452d-4128-98a6-4437df227fec
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0eecebc417a1ddf33f00cdaf5977ca8d3297aca7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069364"
---
# <a name="datasource-data-type-assl"></a>Тип данных DataSource (ASSL)
  Определяет абстрактный примитивный тип данных, представляющий источник данных в [базы данных](../objects/database-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataSource>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <ManagedProvider>...</ManagedProvider>  
   <ConnectionString>...</ConnectionString>  
   <ConnectionStringSecurity>...</ConnectionStringSecurity>  
   <ImpersonationInfo>...</ImpersonationInfo>  
   <Isolation>...</Isolation>  
   <MaxActiveConnections>...</MaxActiveConnections>  
   <Description>...</Description>  
   <Timeout>...</Timeout>  
   <Annotations>...</Annotations>  
   <DataSourcePermission>...</DataSourcePermission>  
</DataSource>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[RelationalDataSource](datasource-data-type-assl.md), [OlapDataSource](olapdatasource-data-type-assl.md), [PushedDataSource](pusheddatasource-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [ConnectionString](../properties/connectionstring-element-assl.md), [ConnectionStringSecurity](../properties/connectionstringsecurity-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DataSourcePermission](../collections/datasourcepermissions-element-assl.md), [Описание](../properties/description-element-assl.md), [идентификатор](../properties/id-element-assl.md), [ImpersonationInfo](../properties/impersonationinfo-element-assl.md), [изоляции](../properties/isolation-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [ManagedProvider](../properties/managedprovider-element-assl.md), [MaxActiveConnections](../properties/maxactiveconnections-element-assl.md), [имя](../properties/name-element-assl.md), [время ожидания](../properties/timeout-element-assl.md)|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 При определении внешних привязок элемент `Name` необязателен. Возможность не указывать элемент `Name` позволяет определять источники данных в рамках привязок для кубов, секций и т. п. `Database` является обязательным элементом для источников данных, содержащихся в элементе `Name`.  
  
 Дополнительные сведения о доступных источниках данных см. в разделе [Источники данных в многомерных моделях](../../multidimensional-models/data-sources-in-multidimensional-models.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.DataSource>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
