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
ms.openlocfilehash: 71396a071a42d7dd40a6537a2834541aab2b6bad
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921096"
---
# <a name="ado-dynamic-properties"></a>Динамические свойства ADO
Динамические свойства могут быть добавлены к коллекциям [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) [соединения](../../../ado/reference/ado-api/connection-object-ado.md), [команды](../../../ado/reference/ado-api/command-object-ado.md)или объектов [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) . Источником этих свойств является либо поставщик данных, например [поставщик OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), либо поставщик услуг, например [Служба курсора Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md). Дополнительные сведения о конкретном динамическом свойстве см. в документации соответствующего поставщика данных или поставщика услуг.  
  
 [Индекс динамического свойства ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) обеспечивает перекрестную ссылку между именами ADO и OLE DB для каждого динамического свойства стандартного поставщика OLE DB.  
  
 Следующие динамические свойства особенно интересны, они также описаны в источниках, упомянутых ранее. Специальные функции ADO описаны в подразделах справки ADO в следующем списке.  
  
|||  
|-|-|  
|[Увеличить](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Указывает, следует ли создавать индекс для этого поля.|  
|[Предупреждение](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)|Указывает, должен ли поставщик OLE DB запрашивать сведения об инициализации у пользователя.|  
|[Изменить имя формы](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Задает имя объекта **набора записей** .|  
|[Команда повторной синхронизации](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Указывает указанную пользователем строку команды, которая выдается методом повторной **синхронизации** для обновления данных в таблице, указанной в динамическом свойстве **уникальной таблицы** .|  
|[Уникальная таблица, уникальная схема, уникальный каталог](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**Уникальная таблица** Указывает имя базовой таблицы, в которой разрешены обновления, вставки и удаления.<br /><br /> **Уникальная схема** Указывает схему или имя владельца таблицы.<br /><br /> **Уникальный каталог** Указывает каталог или имя базы данных, содержащей таблицу.|  
|[Повторная синхронизация обновлений](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)|Указывает, следует ли за методом **UpdateBatch** выполнить неявную операцию повторной **синхронизации** , и если да, то область действия этой операции.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Коллекции ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Перечислимые константы ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты и интерфейсы ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
