---
title: Метод SubmitChanges (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SubmitChanges method [ADO]
ms.assetid: 250062a4-13c4-4bed-807d-8b9ad81536d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0a5beeef5d88a30496a8b706dcfd7ffabb931b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47744483"
---
# <a name="submitchanges-method-rds"></a>Метод SubmitChanges (служба удаленных рабочих столов)
Ожидающие изменения локально кэшированных и обновляемые [записей](../../../ado/reference/ado-api/recordset-object-ado.md) к источнику данных, указанной в [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойство или [URL-адрес](../../../ado/reference/rds-api/url-property-rds.md) свойство.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *Фабрики данных*  
 Объектную переменную, которая представляет [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта.  
  
 *Соединение*  
 Объект **строка** значение, представляющее соединение, созданное с помощью **RDS. DataControl** объекта [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойство.  
  
 *Набор записей*  
 Объектную переменную, которая представляет **записей** объекта.  
  
## <a name="remarks"></a>Примечания  
 [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md), и [SQL](../../../ado/reference/rds-api/sql-property.md) свойства должны быть установлены перед использованием **SubmitChanges** метод с  **RDS. DataControl** объекта.  
  
 При вызове метода [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) метод после вызова **SubmitChanges** для того же **записей** объекта, **CancelUpdate** вызов завершается ошибкой, так как изменения уже были зафиксированы.  
  
 Измененные записи отправляются для изменения, а также всех изменений, успешном завершении или сбое все изменения, вместе.  
  
 Можно использовать **SubmitChanges** только со значением по умолчанию **RDSServer.DataFactory** объекта. Этот метод нельзя использовать настраиваемые бизнес-объекты.  
  
 Если **URL-адрес** свойство задано, **SubmitChanges** будет отправить изменения в расположение, указанное в URL-адресом.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>См. также  
 [Пример метода SubmitChanges (VBScript)](../../../ado/reference/rds-api/submitchanges-method-example-vbscript.md)   
 [Кнопки команд адресной книги](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Метод CancelUpdate (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Метод Refresh (служба удаленных рабочих столов)](../../../ado/reference/rds-api/refresh-method-rds.md)



