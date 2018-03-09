---
title: "Динамические свойства ADO | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic properties [ADO]
- properties [ADO], dynamic
ms.assetid: d7b06d72-f792-4328-93a2-5006b9e2c581
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 254372b292229f5ab65dacdbf1b021209a8ecb9a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="ado-dynamic-properties"></a>Динамические свойства ADO
Динамические свойства, которые могут добавляться в [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [команда](../../../ado/reference/ado-api/command-object-ado.md), или [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объектов. Источник для этих свойств — либо поставщик данных, таких как [поставщик OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), или поставщика услуг, таких как [службы курсора для OLE DB Microsoft](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md). Ссылаться на подходящий поставщик данных или документации по поставщику службы Дополнительные сведения о конкретных динамических свойств.  
  
 [Индекс динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) предоставляет перекрестной ссылки между именами ADO и OLE DB для каждой стандартной OLE DB поставщик динамических свойств.  
  
 Следующие динамические свойства особенно интересны, а также описаны в приведенных выше источниках. В ADO разделы справки в следующем списке описана специальные функциональные возможности с помощью ADO.  
  
|||  
|-|-|  
|[Оптимизация](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Указывает, следует ли создавать индекс для этого поля.|  
|[Prompt](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)|Указывает, должен ли поставщик OLE DB запрашивать у пользователя сведения об инициализации.|  
|[Изменить имя](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Указывает имя для **записей** объекта.|  
|[Команда синхронизации](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Указывает команду, предоставленные пользователем строкой, которую **Resync** проблем метода для обновления данных в таблице, указанной в **уникальной таблицы** динамических свойств.|  
|[Уникальной таблицы, уникальную схему, уникальный каталог](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**Уникальной таблицы** указывает имя базовой таблицы, на которой разрешены обновления, вставки и удаления.<br /><br /> **Уникальной схемы** указывает схему, или имя владельца таблицы.<br /><br /> **Уникальный каталог** указывает каталог или имя базы данных, содержащую таблицу.|  
|[Повторная синхронизация обновлений](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)|Указывает ли **UpdateBatch** метод следуют неявный **Resync** метод операцию и если да, область данной операции.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO коллекций](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO перечисляемые константы](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты ADO и интерфейсы](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
