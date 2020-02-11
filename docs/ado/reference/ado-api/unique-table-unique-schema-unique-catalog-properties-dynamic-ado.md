---
title: Управление изменениями в базовой таблице набора записей (ADO) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67911683"
---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Уникальная таблица, уникальная схема, свойства уникального каталога — Dynamic (ADO)
Позволяет точно управлять изменениями в определенной базовой таблице в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md) , сформированном операцией Join над несколькими базовыми таблицами.  
  
-   **Уникальная таблица** указывает имя базовой таблицы, в которой разрешены обновления, вставки и удаления.  
  
-   **Уникальная схема** указывает *схему*или имя владельца таблицы.  
  
-   **Уникальный каталог** указывает *Каталог*или имя базы данных, содержащей таблицу.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение, которое является именем таблицы, схемы или каталога.  
  
## <a name="remarks"></a>Remarks  
 Требуемая базовая таблица уникально идентифицируется по именам каталогов, схем и таблиц. Если задано свойство **уникальной таблицы** , то для поиска базовой таблицы используются значения **уникальной схемы** или свойства **уникального каталога** . Он предназначен, но не является обязательным, так как либо **уникальная схема** , либо свойства **уникального каталога** задаются до того, как будет задано свойство **уникальной таблицы** .  
  
 Первичный ключ **уникальной таблицы** рассматривается как первичный ключ всего **набора записей**. Это ключ, используемый для любого метода, для которого необходим первичный ключ.  
  
 Если задана **уникальная таблица** , метод [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md) влияет только на именованную таблицу. Методы [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [Update](../../../ado/reference/ado-api/update-method.md)и [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) влияют на все соответствующие базовые таблицы **набора записей**.  
  
 Перед выполнением пользовательских повторных синхронизаций необходимо указать **уникальную таблицу** . Если не указана **уникальная таблица** , то свойство [Command](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) повторной синхронизации не будет действовать.  
  
 Если не удается найти уникальную базовую таблицу, возникает ошибка во время выполнения.  
  
 Эти динамические свойства добавляются к коллекции [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) объекта **Recordset** , если свойство [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) имеет значение **адусеклиент**.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
