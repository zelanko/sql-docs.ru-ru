---
title: "Метод CancelUpdate (RDS) | Документы Microsoft"
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
- CancelUpdate method [RDS]
ms.assetid: 76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9b8e41e0cd963b87b73fc65b3f149f22f3a67b76
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="cancelupdate-method-rds"></a>Метод CancelUpdate (RDS)
Отменяет все изменения, внесенные в текущем или новом строку из [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.CancelUpdate  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
## <a name="remarks"></a>Замечания  
 Служба курсора для OLE DB сохраняет как копия исходных значений и кэш изменений. При вызове **CancelUpdate**кэша изменений задается равным пустой и любые связанные элементы управления, обновляются с исходными данными.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода CancelUpdate (VBScript)](../../../ado/reference/rds-api/cancelupdate-method-example-vbscript.md)   
 [Адрес книги кнопки](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Метод Cancel (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Метод Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Обновить метод (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Метод SubmitChanges (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



