---
title: "Метод макрокоманду УдалитьЗапись (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords: DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 66d13bc4449bad73b1ab09869a764e6bff533442
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="deleterecord-method-ado"></a>Метод макрокоманду УдалитьЗапись (ADO)
Удаление сущности, представленной [записи](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательно. Объект **строка** значение, содержащее URL-адрес идентифицирует сущность (например, файл или каталог) для удаления. Если *источника* опущен или указывает на пустую строку, сущности, представленной текущим [записи](../../../ado/reference/ado-api/record-object-ado.md) удаляется. Если запись является записью коллекции ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md) из **adCollectionRecord**, такие как каталог) также будут удалены все дочерние элементы (например, вложенные папки).  
  
 *Асинхронный*  
 Необязательно. Объект **логическое** значением, которое при **True**, указывает, что асинхронная операция удаления.  
  
## <a name="remarks"></a>Замечания  
 Операции на объект, представленный этим **записи** может завершиться ошибкой после завершения этого метода. После вызова метода **макрокоманду УдалитьЗапись**, **запись** должен быть закрыт, поскольку поведение **записи** могут стать непредсказуемыми зависимости при обновлении поставщика **Записи** с источником данных.  
  
 Если этот **запись** были получены из [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md), а затем результаты этой операции не будут отражены немедленно, в **набора записей**. Обновить **записей** , закрытия и повторного открытия или выполнив **записей** [Requery](../../../ado/reference/ado-api/requery-method.md) метод, [обновления](../../../ado/reference/ado-api/update-method.md) метод, или [Resync](../../../ado/reference/ado-api/resync-method.md) метод.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод Delete (ADO поля коллекции)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Метод Delete (объект Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
