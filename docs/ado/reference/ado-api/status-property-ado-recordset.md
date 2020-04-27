---
title: Свойство Status (набор записей ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1d91c3e92be7679ad6fbbb4a4ee7bd1bb6a48422
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67916838"
---
# <a name="status-property-ado-recordset"></a>Свойство Status (объект Recordset ADO)
Указывает состояние текущей записи по отношению к пакетным обновлениям или другим массовым операциям.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает сумму одного или нескольких значений [рекордстатусенум](../../../ado/reference/ado-api/recordstatusenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **Status** , чтобы узнать, какие изменения ожидаются для записей, измененных во время пакетного обновления. Свойство **Status** можно также использовать для просмотра состояния записей, которые не удалось выполнить в ходе выполнения операций с массовыми операциями, например при вызове методов [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) для объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) или при установке свойства [фильтра](../../../ado/reference/ado-api/filter-property.md) для объекта **набора записей** в массив закладок. С помощью этого свойства можно определить, каким образом заданная запись не удалась, и устранить ее соответствующим образом.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Status (набор записей) (VB)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Пример свойства Status (Visual C++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
