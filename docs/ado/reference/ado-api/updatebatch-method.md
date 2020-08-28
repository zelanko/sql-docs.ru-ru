---
description: Метод UpdateBatch
title: Метод UpdateBatch | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 648e6f8e64d4001851afb3838c901ab2b1172108
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988005"
---
# <a name="updatebatch-method"></a>Метод UpdateBatch
Записывает все ожидающие пакетные обновления на диск.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>Параметры  
 *аффектрекордс*  
 Необязательный элемент. Значение [аффектенум](./affectenum.md) , указывающее, сколько записей будет влиять на метод **UpdateBatch** .  
  
 *пресервестатус*  
 Необязательный элемент. **Логическое** значение, указывающее, должны ли быть зафиксированы локальные изменения, указанные в свойстве [Status](./status-property-ado-recordset.md) . Если это значение равно **true**, свойство **Status** каждой записи остается неизменным после завершения обновления.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **UpdateBatch** при изменении объекта **набора записей** в режиме пакетного обновления для передачи всех изменений, внесенных в объект **набора записей** , в основную базу данных.  
  
 Если объект **Recordset** поддерживает пакетное обновление, можно кэшировать несколько изменений в одной или нескольких записях локально, пока не будет вызван метод **UpdateBatch** . Если вы изменяете текущую запись или добавляете новую запись при вызове метода **UpdateBatch** , ADO автоматически вызывает метод [Update](./update-method.md) , чтобы сохранить все ожидающие изменения в текущей записи перед передачей пакетных изменений поставщику. Пакетное обновление следует использовать только с курсором KEYSET или static.  
  
> [!NOTE]
>  Указание **адаффектграуп** в качестве значения для этого параметра приведет к ошибке, если в текущем **наборе записей** нет видимых записей (например, фильтра, для которого не совпадают записи).  
  
 Если попытка передать изменения для всех или всех записей завершается неудачей из-за конфликта с базовыми данными (например, запись уже удалена другим пользователем), поставщик возвращает предупреждения в коллекцию [ошибок](./errors-collection-ado.md) и возникает ошибка времени выполнения. Используйте свойство [Filter](./filter-property.md) (**адфилтераффектедрекордс**) и свойство [Status](./status-property-ado-recordset.md) для обнаружения записей с конфликтами.  
  
 Чтобы отменить все отложенные обновления пакетов, используйте метод [CancelBatch](./cancelbatch-method-ado.md) .  
  
 Если задана [уникальная таблица](./unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и динамические свойства повторной [синхронизации обновления](./update-resync-property-dynamic-ado.md) , а **набор записей** является результатом выполнения операции JOIN над несколькими таблицами, то при выполнении метода **UpdateBatch** в зависимости от параметров свойства " [Обновить повторную](./update-resync-property-dynamic-ado.md) синхронизацию" неявно следует метод повторной [синхронизации](./resync-method.md) .  
  
 Порядок, в котором отдельные обновления пакета выполняются в источнике данных, не обязательно совпадает с порядком, в котором они были выполнены в локальном **наборе записей**. Порядок обновления зависит от поставщика. Примите это во внимание при программировании обновлений, связанных друг с другом, таких как ограничения внешнего ключа при вставке или обновлении.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов UpdateBatch и CancelBatch (Visual Basic)](./updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Примеры методов UpdateBatch и CancelBatch (Visual c++)](./updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Метод CancelBatch (ADO)](./cancelbatch-method-ado.md)   
 [Метод Clear (ADO)](./clear-method-ado.md)   
 [Свойство LockType (ADO)](./locktype-property-ado.md)   
 [Метод Update](./update-method.md)