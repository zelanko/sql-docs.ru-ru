---
description: Метод CancelUpdate (служба удаленных рабочих столов)
title: Метод CancelUpdate (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CancelUpdate method [RDS]
ms.assetid: 76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b0234a240d863f52d33fe1eb230bcfc11eadf06
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88768753"
---
# <a name="cancelupdate-method-rds"></a>Метод CancelUpdate (служба удаленных рабочих столов)
Отменяет все изменения, внесенные в текущую или новую строку объекта [набора записей](../ado-api/recordset-object-ado.md) .  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.CancelUpdate  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](./datacontrol-object-rds.md) .  
  
## <a name="remarks"></a>Remarks  
 Служба курсора для OLE DB сохраняет копию исходных значений и кэш изменений. При вызове **CancelUpdate**кэш изменений сбрасывается в пустое состояние, а все привязанные элементы управления обновляются исходными данными.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода CancelUpdate (VBScript)](./cancelupdate-method-example-vbscript.md)   
 [Кнопки для команд адресной книги](../../guide/remote-data-service/address-book-command-buttons.md)   
 [Метод Cancel (ADO)](../ado-api/cancel-method-ado.md)   
 [Метод Cancel (RDS)](./cancel-method-rds.md)   
 [Метод CancelBatch (ADO)](../ado-api/cancelbatch-method-ado.md)   
 [Метод CancelUpdate (ADO)](../ado-api/cancelupdate-method-ado.md)   
 [Метод Refresh (RDS)](./refresh-method-rds.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](./submitchanges-method-rds.md)