---
title: Метод (RDS) Refresh | Документация Майкрософт
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
f1_keywords:
- Refresh
- RDS.DataControl::Refresh
- DataControl::Refresh
helpviewer_keywords:
- Refresh method [RDS]
ms.assetid: c90a8050-0ff4-4c83-9925-261f2f2ccfe9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 822430c56070bb459e36ca3a3310d186258aea34
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601925"
---
# <a name="refresh-method-rds"></a>Метод Refresh (служба удаленных рабочих столов)
Повторно запрашивает источник данных, указанный в [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойство и обновления результатов запроса.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
## <a name="remarks"></a>Примечания  
 Необходимо задать [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md), и [SQL](../../../ado/reference/rds-api/sql-property.md) свойства, прежде чем использовать **обновить** метод. Все элементы управления с привязкой к данным на форму, связанную с **RDS. DataControl** объекта будут отражены в новом наборе записей. Все ранее существовавшие [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект будет освобожден, а все несохраненные изменения будут утеряны. **Обновить** метод автоматически делает первую запись текущей записи.  
  
 Рекомендуется вызывать **обновить** метод периодически при работе с данными. Если извлечение данных и оставить его на клиентском компьютере какое-то время, это может устареть. Вполне возможно, что любые изменения, внесенные не удастся, так как другой пользователь изменил запись и отправил изменения, прежде чем.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Метод пример Refresh (Visual Basic)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Обновить пример метода (VBScript)](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [Кнопки команд адресной книги](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Метод CancelUpdate (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


