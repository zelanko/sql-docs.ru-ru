---
title: Динамические свойства ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dynamic properties [ADO]
- properties [ADO], dynamic
ms.assetid: d7b06d72-f792-4328-93a2-5006b9e2c581
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2ad6c2804b70011380a12b5b9e0cd1f52fd56398
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696864"
---
# <a name="ado-dynamic-properties"></a>Динамические свойства ADO
Динамические свойства, которые могут добавляться к [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [команда](../../../ado/reference/ado-api/command-object-ado.md), или [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объектов. Источником для этих свойств является либо поставщик данных, таких как [поставщик OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), или к поставщику услуг, таких как [служба курсора Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md). Укажите ссылку на подходящий поставщик данных или документации по поставщику службы Дополнительные сведения об определенном свойстве динамического.  
  
 [Индекс динамических свойств ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) предоставляет перекрестной ссылки между именами ADO и OLE DB для каждого стандартный OLE DB поставщика динамические свойства.  
  
 Следующие динамические свойства особенно интересны, а также описаны в приведенных выше источниках. Специальные функции с помощью ADO описана в разделах справки ADO в списке ниже.  
  
|||  
|-|-|  
|[Оптимизация](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Указывает, должен ли быть создан индекс в этом поле.|  
|[Запрос](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)|Указывает, должен ли поставщик OLE DB запрашивать пользователя сведения об инициализации.|  
|[Изменить имя](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Указывает имя для **записей** объекта.|  
|[Команда синхронизации](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Указывает пользовательские команды-строка, **Resync** проблем метода для обновления данных в таблице, указанной в **уникальной таблицы** динамических свойств.|  
|[Уникальная таблица, уникальная схема, уникальный каталог](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**Уникальная таблица** указывает имя базовой таблицы, на которой разрешены обновления, вставки и удаления.<br /><br /> **Уникальная схема** указывает схему, или имя владельца таблицы.<br /><br /> **Уникальный каталог** указывает каталог или имя базы данных, содержащую таблицу.|  
|[Повторная синхронизация обновления](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)|Указывает ли **UpdateBatch** метод сопровождается неявным **Resync** работы метода и если да, область этой операции.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Коллекции ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Перечисляемые константы ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. Ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты и интерфейсы ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
