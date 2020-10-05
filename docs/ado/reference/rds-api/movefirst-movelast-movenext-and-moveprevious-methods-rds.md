---
description: Методы MoveFirst, MoveLast, MoveNext и MovePrevious (служба удаленных рабочих столов)
title: Методы MoveFirst, MoveLast, MoveNext и MovePrevious (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- MoveLast method [RDS]
- MovePrevious method [RDS]
- MoveFirst method [RDS]
- MoveNext method [RDS]
ms.assetid: 45c80bb5-136f-4204-9df2-78740fa55574
author: rothja
ms.author: jroth
ms.openlocfilehash: e0e2b53967017ca093b04b5449ebd7a47a983f29
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724475"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-rds"></a>Методы MoveFirst, MoveLast, MoveNext и MovePrevious (служба удаленных рабочих столов)
Переход к первой, последней, следующей или предыдущей записи в указанном объекте [набора записей](../ado-api/recordset-object-ado.md) .  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.Recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](./datacontrol-object-rds.md) .  
  
## <a name="remarks"></a>Комментарии  
 Методы **Move** можно использовать с **RDS. Объект элемента управления** данными для перемещения по записям данных в элементах управления с привязкой к данным на веб-странице. Например, предположим, что **набор записей** отображается в сетке путем привязки к **RDS. Объект элемента управления** . Затем можно включить кнопки «Первая», «последняя», «вперед» и «назад», которые пользователи могут нажать для перехода к первой, последней, следующей или предыдущей записи в отображаемом **наборе записей**. Это делается путем вызова методов **MoveFirst**, **MoveLast**, **MoveNext**и **MovePrevious** **RDS. Объект элемента управления** DataObject в процедурах OnClick для первой, последней, следующей и предыдущей кнопок соответственно. В [примере адресной книги](../../guide/remote-data-service/address-book-navigation-buttons.md) показано, как это сделать.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Move (ADO)](../ado-api/move-method-ado.md)   
 [Методы MoveFirst, MoveLast, MoveNext и MovePrevious (ADO)](../ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [Метод MoveRecord (ADO)](../ado-api/moverecord-method-ado.md)