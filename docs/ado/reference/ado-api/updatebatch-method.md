---
description: Метод UpdateBatch
title: Метод UpdateBatch | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::UpdateBatch
- Recordset15::raw_UpdateBatch
helpviewer_keywords:
- UpdateBatch method [ADO]
ms.assetid: 23f9314c-b027-4a51-aeae-50caa2977740
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f0a730a64a34e13f5a7554ecb700ab1e555a77d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441606"
---
# <a name="updatebatch-method"></a>Метод UpdateBatch
Записывает все ожидающие пакетные обновления на диск.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>Параметры  
 *аффектрекордс*  
 Необязательный параметр. Значение [аффектенум](../../../ado/reference/ado-api/affectenum.md) , указывающее, сколько записей будет влиять на метод **UpdateBatch** .  
  
 *пресервестатус*  
 Необязательный параметр. **Логическое** значение, указывающее, должны ли быть зафиксированы локальные изменения, указанные в свойстве [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) . Если это значение равно **true**, свойство **Status** каждой записи остается неизменным после завершения обновления.  
  
## <a name="remarks"></a>Комментарии  
 Используйте метод **UpdateBatch** при изменении объекта **набора записей** в режиме пакетного обновления для передачи всех изменений, внесенных в объект **набора записей** , в основную базу данных.  
  
 Если объект **Recordset** поддерживает пакетное обновление, можно кэшировать несколько изменений в одной или нескольких записях локально, пока не будет вызван метод **UpdateBatch** . Если вы изменяете текущую запись или добавляете новую запись при вызове метода **UpdateBatch** , ADO автоматически вызывает метод [Update](../../../ado/reference/ado-api/update-method.md) , чтобы сохранить все ожидающие изменения в текущей записи перед передачей пакетных изменений поставщику. Пакетное обновление следует использовать только с курсором KEYSET или static.  
  
> [!NOTE]
>  Указание **адаффектграуп** в качестве значения для этого параметра приведет к ошибке, если в текущем **наборе записей** нет видимых записей (например, фильтра, для которого не совпадают записи).  
  
 Если попытка передать изменения для всех или всех записей завершается неудачей из-за конфликта с базовыми данными (например, запись уже удалена другим пользователем), поставщик возвращает предупреждения в коллекцию [ошибок](../../../ado/reference/ado-api/errors-collection-ado.md) и возникает ошибка времени выполнения. Используйте свойство [Filter](../../../ado/reference/ado-api/filter-property.md) (**адфилтераффектедрекордс**) и свойство [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) для обнаружения записей с конфликтами.  
  
 Чтобы отменить все отложенные обновления пакетов, используйте метод [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) .  
  
 Если задана [уникальная таблица](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и динамические свойства повторной [синхронизации обновления](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) , а **набор записей** является результатом выполнения операции JOIN над несколькими таблицами, то при выполнении метода **UpdateBatch** в зависимости от параметров свойства " [Обновить повторную](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) синхронизацию" неявно следует метод повторной [синхронизации](../../../ado/reference/ado-api/resync-method.md) .  
  
 Порядок, в котором отдельные обновления пакета выполняются в источнике данных, не обязательно совпадает с порядком, в котором они были выполнены в локальном **наборе записей**. Порядок обновления зависит от поставщика. Примите это во внимание при программировании обновлений, связанных друг с другом, таких как ограничения внешнего ключа при вставке или обновлении.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов UpdateBatch и CancelBatch (Visual Basic)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Примеры методов UpdateBatch и CancelBatch (Visual c++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Свойство LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
