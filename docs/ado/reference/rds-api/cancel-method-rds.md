---
title: Cancel-метод (RDS) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Cancel method [RDS]
ms.assetid: 560b5b3d-fba9-4275-8920-9c3e186134f7
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba0a169bf4c5a2438dca0672fef785766bae2503
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="cancel-method-rds"></a>Метод Cancel (RDS)
Отменяет выполнение ожидающих вызова асинхронного метода.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RDS.DataControl.Cancel  
```  
  
## <a name="remarks"></a>Замечания  
 При вызове **отменить**, [состояние готовности](../../../ado/reference/rds-api/readystate-property-rds.md) автоматически устанавливается значение **adcReadyStateLoaded**и [записей](../../../ado/reference/ado-api/recordset-object-ado.md) будет пустым.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Cancel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Метод Cancel (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Свойство ExecuteOptions (служба удаленных рабочих столов)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


