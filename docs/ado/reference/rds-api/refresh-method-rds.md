---
title: "Обновить метод (RDS) | Документы Microsoft"
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
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9710779f8ac92b4e9696ec56997c4eea43032206
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
 [Объект DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [Обновить пример метода (Visual Basic)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Обновить пример метода (VBScript)](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [Адрес книги кнопки](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Обновить метод (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [Метод SubmitChanges (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



