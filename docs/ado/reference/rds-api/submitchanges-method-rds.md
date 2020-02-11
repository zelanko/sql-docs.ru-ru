---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 783ad55a2355759f7625d536272f5243cd1c61c4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963280"
---
# <a name="submitchanges-method-rds"></a>Метод SubmitChanges (служба удаленных рабочих столов)
Отправляет ожидающие изменения локально кэшированного и обновляемого [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) в источник данных, указанный в свойстве [Connect](../../../ado/reference/rds-api/connect-property-rds.md) или в свойстве [URL-адреса](../../../ado/reference/rds-api/url-property-rds.md) .  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *Фабрика данных*  
 Объектная переменная, представляющая объект [RDSServer.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) DataObject.  
  
 *Соединен*  
 **Строковое** значение, представляющее соединение, созданное с помощью **RDS. **Свойство [соединения](../../../ado/reference/rds-api/connect-property-rds.md) объекта элемента управления DataObject.  
  
 *набор записей*  
 Объектная переменная, представляющая объект **набора записей** .  
  
## <a name="remarks"></a>Remarks  
 Прежде чем использовать метод **SubmitChanges** с RDS, необходимо задать свойства [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md)и [SQL](../../../ado/reference/rds-api/sql-property.md) **. Объект элемента управления** .  
  
 Если метод [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) вызывается после вызова **SubmitChanges** для того же объекта **Recordset** , вызов **CancelUpdate** завершается ошибкой, поскольку изменения уже были зафиксированы.  
  
 Для изменения отправляются только измененные записи, либо все изменения успешно выполнены, либо все изменения завершаются сбоем.  
  
 **SubmitChanges** можно использовать только с объектом **RDSServer.** DataObject, используемым по умолчанию. Пользовательские бизнес-объекты не могут использовать этот метод.  
  
 Если свойство **URL** задано, **SubmitChanges** отправит изменения в расположение, указанное URL-адресом.  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>См. также:  
 [Пример метода SubmitChanges (VBScript)](../../../ado/reference/rds-api/submitchanges-method-example-vbscript.md)   
 [Кнопки для команд адресной книги](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Метод Refresh (служба удаленных рабочих столов)](../../../ado/reference/rds-api/refresh-method-rds.md)



