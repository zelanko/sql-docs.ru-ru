---
description: Метод SubmitChanges (служба удаленных рабочих столов)
title: Метод SubmitChanges (RDS) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 86645c9a8735c8764bbd210e55858a6de81e387d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767363"
---
# <a name="submitchanges-method-rds"></a>Метод SubmitChanges (служба удаленных рабочих столов)
Отправляет ожидающие изменения локально кэшированного и обновляемого [набора записей](../ado-api/recordset-object-ado.md) в источник данных, указанный в свойстве [Connect](./connect-property-rds.md) или в свойстве [URL-адреса](./url-property-rds.md) .  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](./datacontrol-object-rds.md) .  
  
 *DataFactory*  
 Объектная переменная, представляющая объект [RDSServer.](./datafactory-object-rdsserver.md) DataObject.  
  
 *Соединение*  
 **Строковое** значение, представляющее соединение, созданное с помощью **RDS. **Свойство [соединения](./connect-property-rds.md) объекта элемента управления DataObject.  
  
 *набор записей*  
 Объектная переменная, представляющая объект **набора записей** .  
  
## <a name="remarks"></a>Remarks  
 Прежде чем использовать метод **SubmitChanges** с RDS, необходимо задать свойства [Connect](./connect-property-rds.md), [Server](./server-property-rds.md)и [SQL](./sql-property.md) **. Объект элемента управления** .  
  
 Если метод [CancelUpdate](./cancelupdate-method-rds.md) вызывается после вызова **SubmitChanges** для того же объекта **Recordset** , вызов **CancelUpdate** завершается ошибкой, поскольку изменения уже были зафиксированы.  
  
 Для изменения отправляются только измененные записи, либо все изменения успешно выполнены, либо все изменения завершаются сбоем.  
  
 **SubmitChanges** можно использовать только с объектом **RDSServer.** DataObject, используемым по умолчанию. Пользовательские бизнес-объекты не могут использовать этот метод.  
  
 Если свойство **URL** задано, **SubmitChanges** отправит изменения в расположение, указанное URL-адресом.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
    :::column-end:::
    :::column:::
        [Объект DataFactory (RDSServer)](./datafactory-object-rdsserver.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример метода SubmitChanges (VBScript)](./submitchanges-method-example-vbscript.md)   
 [Кнопки для команд адресной книги](../../guide/remote-data-service/address-book-command-buttons.md)   
 [Метод CancelUpdate (RDS)](./cancelupdate-method-rds.md)   
 [Метод Refresh (служба удаленных рабочих столов)](./refresh-method-rds.md)