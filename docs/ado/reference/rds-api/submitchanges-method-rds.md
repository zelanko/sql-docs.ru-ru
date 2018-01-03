---
title: "Метод SubmitChanges (RDS) | Документы Microsoft"
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: SubmitChanges method [ADO]
ms.assetid: 250062a4-13c4-4bed-807d-8b9ad81536d4
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fc04a3ac77d6363c86f684b474fb5fa9a06c3c5e
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="submitchanges-method-rds"></a>Метод SubmitChanges (RDS)
Ожидающие изменения локально кэшированных и обновляемые [записей](../../../ado/reference/ado-api/recordset-object-ado.md) к источнику данных, указанному в [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойство или [URL-адрес](../../../ado/reference/rds-api/url-property-rds.md) свойство.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *DataFactory*  
 Объектную переменную, которая представляет [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта.  
  
 *Соединение*  
 Объект **строка** значение, представляющее соединение, созданное с помощью **RDS. DataControl** объекта [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойство.  
  
 *Набор записей*  
 Объектную переменную, которая представляет **записей** объекта.  
  
## <a name="remarks"></a>Remarks  
 [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [сервера](../../../ado/reference/rds-api/server-property-rds.md), и [SQL](../../../ado/reference/rds-api/sql-property.md) свойства должны быть заданы, прежде чем использовать **SubmitChanges** метод с  **RDS. DataControl** объекта.  
  
 При вызове метода [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) метод после вызова **SubmitChanges** для той же **записей** объекта, **CancelUpdate** вызов завершается ошибкой, так как изменения уже были зафиксированы.  
  
 Измененные записи отправляются для изменения и всех изменений, успех или неудача все изменения, вместе.  
  
 Можно использовать **SubmitChanges** только со значением по умолчанию **RDSServer.DataFactory** объекта. Этот метод нельзя использовать настраиваемые бизнес-объекты.  
  
 Если **URL-адрес** задал свойство **SubmitChanges** будет передать изменения в расположении, указанном в URL-адресе.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>См. также:  
 [Пример метода SubmitChanges (VBScript)](../../../ado/reference/rds-api/submitchanges-method-example-vbscript.md)   
 [Адрес книги кнопки](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Метод Refresh (служба удаленных рабочих столов)](../../../ado/reference/rds-api/refresh-method-rds.md)



