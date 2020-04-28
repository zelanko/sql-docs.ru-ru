---
title: Метод Refresh (RDS) | Документация Майкрософт
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
ms.openlocfilehash: fb7cb94edab6b5422c315b71c2900662f85aa1e2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67963501"
---
# <a name="refresh-method-rds"></a>Метод Refresh (служба удаленных рабочих столов)
Повторно запрашивает источник данных, указанный в свойстве [Connect](../../../ado/reference/rds-api/connect-property-rds.md) , и обновляет результаты запроса.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
## <a name="remarks"></a>Remarks  
 Перед использованием метода **Refresh** необходимо задать свойства [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md)и [SQL](../../../ado/reference/rds-api/sql-property.md) . Все элементы управления, привязанные к данным, в форме, связанной с **RDS. Объект элемента управления** данные будет отражать новый набор записей. Освобождается существующий объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , и все несохраненные изменения отбрасываются. Метод **Refresh** автоматически делает первую запись текущей записью.  
  
 Рекомендуется периодически вызывать метод **Refresh** при работе с данными. Если получить данные и оставить их на клиентском компьютере в течение определенного времени, скорее всего, они устаревают. Возможно, любые внесенные изменения будут завершаться ошибкой, так как другой пользователь мог изменить запись и отправил изменения перед вами.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода Refresh (Visual Basic)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Пример метода Refresh (VBScript)](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [Кнопки для команд адресной книги](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


