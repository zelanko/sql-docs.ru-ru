---
title: Обновить метод (RDS) | Документы Microsoft
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
f1_keywords:
- Refresh
- RDS.DataControl::Refresh
- DataControl::Refresh
helpviewer_keywords:
- Refresh method [RDS]
ms.assetid: c90a8050-0ff4-4c83-9925-261f2f2ccfe9
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 89e9088aeec78213f7da9a79ba78255de4b94b97
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="refresh-method-rds"></a>Обновить метод (RDS)
Вызывает повторный запрос источника данных, указанного в [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойств и обновления результатов запроса.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
## <a name="remarks"></a>Замечания  
 Необходимо задать [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [сервера](../../../ado/reference/rds-api/server-property-rds.md), и [SQL](../../../ado/reference/rds-api/sql-property.md) свойства, прежде чем использовать **обновление** метод. Все элементы управления с привязкой к данным на форму, связанную с **RDS. DataControl** объекта будет отражать нового набора записей. Все предшествующие [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект будет освобожден, а все несохраненные изменения будут отменены. **Обновление** метод автоматически делает первую запись текущей записи.  
  
 Рекомендуется вызывать **обновление** метод периодически при работе с данными. Если извлечение данных и оставить его на клиентский компьютер на некоторое время, вполне вероятно, станут устаревшими. Это возможно, что любые изменения, внесенные завершится ошибкой, так как кто-то другой могли измениться, запись и отправил изменения, прежде чем.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Обновить пример метода (Visual Basic)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Обновить пример метода (VBScript)](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [Адрес книги кнопки](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Обновить метод (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


