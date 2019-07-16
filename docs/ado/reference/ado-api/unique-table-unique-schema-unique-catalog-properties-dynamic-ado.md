---
title: Элемент управления изменяет таблицу базовых записей (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Unique Table property [ADO]
- Unique Schema property [ADO]
- Unique Catalog property [ADO]
ms.assetid: d0e775d8-e353-46a1-ad10-ed4cc240dfaa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1b70920cd223223d5efb14925a6808168ca9cc16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67911683"
---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Уникальная таблица, уникальная схема, уникальный каталог свойства (динамическое) (ADO)
Позволяет точно модификаций элемента управления определенной базовой таблицей в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) , была создана с помощью операции ОБЪЕДИНЕНИЯ на несколько базовых таблиц.  
  
-   **Уникальная таблица** указывает имя базовой таблицы, на которой разрешены обновления, вставки и удаления.  
  
-   **Уникальная схема** указывает *схемы*, или имя владельца таблицы.  
  
-   **Уникальный каталог** указывает *каталога*, или имя базы данных, содержащей таблицу.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, представляющее имя таблицы, схемы или каталога.  
  
## <a name="remarks"></a>Примечания  
 Требуемый базовой таблицы однозначно идентифицируется его каталога, схемы и имена таблиц. Когда **уникальной таблицы** свойство задано, значения **уникальной схемы** или **уникальный каталог** свойства используются для поиска в базовой таблице. Он предназначен, но не является обязательным, одной или обеих **уникальной схемы** и **уникальный каталог** задать свойства перед **уникальной таблицы** свойству.  
  
 Первичный ключ **уникальной таблицы** рассматривается как первичный ключ всего **записей**. Это ключ, который используется для любого метода, требуя первичный ключ.  
  
 Хотя **уникальной таблицы** имеет значение, [удалить](../../../ado/reference/ado-api/delete-method-ado-recordset.md) метод затрагивает только именованную таблицу. [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [обновление](../../../ado/reference/ado-api/update-method.md), и [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) методы влияют на все соответствующие базовые таблицы из **Записей**.  
  
 **Уникальная таблица** должны быть указаны до выполнения любого пользовательского синхронизаций. Если **уникальной таблицы** не указан, [Resync команда](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) свойство не окажет никакого воздействия.  
  
 Ошибка времени выполнения возникает, если не удается найти уникальный базовой таблицы.  
  
 Эти динамические свойства добавляются к **записей** объект [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции при [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству  **adUseClient**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
