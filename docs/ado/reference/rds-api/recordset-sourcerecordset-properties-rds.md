---
title: Набор записей, свойства SourceRecordset (RDS) | Документы Microsoft
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Recordset property [ADO]
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e934983f54be5644e945e4ecdcf201b793c33ea4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="recordset-sourcerecordset-properties-rds"></a>Набор записей, свойства SourceRecordset (RDS)
Указывает **записей** объект, возвращенный пользовательский бизнес-объект.  
  
 **Область применения:** [DataControl объекта (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *Набор записей*  
 Объектную переменную, которая представляет **записей** объекта.  
  
## <a name="remarks"></a>Замечания  
 Можно задать **SourceRecordset** свойства [записей](../../../ado/reference/ado-api/recordset-object-ado.md) возвращенные пользовательский бизнес-объект.  
  
 Эти свойства позволяют приложению обрабатывать процесс привязки с помощью пользовательского процесса. Они получают набор строк, заключенное в **набора записей** , чтобы вы могли взаимодействовать напрямую с **набора записей**, выполнение действий, таких как установка свойств или прохода **набора записей** .  
  
 Можно задать **SourceRecordset** свойства или чтения **записей** свойства во время выполнения в коде сценария.  
  
 **SourceRecordset** является свойством только для записи, отличается от **записей** свойство, которое является свойством только для чтения.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Набор записей и пример использования свойств SourceRecordset (VBScript)](../../../ado/reference/rds-api/recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [Метод CreateRecordset (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)   
 [Метод Query (служба удаленных рабочих столов)](../../../ado/reference/rds-api/query-method-rds.md)


