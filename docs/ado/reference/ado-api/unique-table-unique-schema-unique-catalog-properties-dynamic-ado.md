---
title: "Элемент управления изменений в таблице базового набора записей (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Unique Table property [ADO]
- Unique Schema property [ADO]
- Unique Catalog property [ADO]
ms.assetid: d0e775d8-e353-46a1-ad10-ed4cc240dfaa
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: da2f70b0f3d6f1ae3983e44f26191e13cc26f5a2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Уникальной таблицы, уникальную схему уникальный каталога динамические свойства (ADO)
Позволяет точно управления изменения определенной базовой таблицей в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) , была создана с помощью операции СОЕДИНЕНИЯ на нескольких базовых таблицах.  
  
-   **Уникальной таблицы** указывает имя базовой таблицы, на которой разрешены обновления, вставки и удаления.  
  
-   **Уникальную схему** указывает *схемы*, или имя владельца таблицы.  
  
-   **Уникальный каталог** указывает *каталога*, или имя базы данных, содержащей таблицу.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, представляющее имя таблицы, схемы или каталога.  
  
## <a name="remarks"></a>Замечания  
 Требуемый базовой таблицы однозначно идентифицируется его каталога, схемы и имена таблиц. Когда **уникальной таблицы** свойство задано, значения **уникальную схему** или **уникальный каталог** свойства используются для поиска в базовой таблице. Он предназначен, но не является обязательным, одной или обеих **уникальную схему** и **уникальный каталог** задать свойства перед **уникальной таблицы** свойству.  
  
 Первичный ключ **уникальной таблицы** рассматривается как первичный ключ всей **записей**. Это ключ, используемый для любого метода, требующие первичный ключ.  
  
 Хотя **уникальной таблицы** имеет значение [удалить](../../../ado/reference/ado-api/delete-method-ado-recordset.md) метод влияет только на именованные таблицу. [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [обновление](../../../ado/reference/ado-api/update-method.md), и [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) методы влияют на все соответствующие базовые таблицы из **Записей**.  
  
 **Уникальной таблицы** необходимо указать перед выполнением любой пользовательский повторной синхронизацией. Если **уникальной таблицы** не указан, [Resync команда](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) свойство не будет действовать.  
  
 Ошибка во время выполнения возникает, если не удается найти уникальный базовой таблицы.  
  
 Эти динамические свойства добавляются к **записей** объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции при [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству  **adUseClient**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)

