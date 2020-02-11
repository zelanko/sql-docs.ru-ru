---
title: Свойство MarshalOptions (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MarshalOptions
helpviewer_keywords:
- MarshalOptions property [ADO]
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0212f3b4cb663bd56adaa1bdbc3ab6675c3ce888
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932272"
---
# <a name="marshaloptions-property-ado"></a>Свойство MarshalOptions (ADO)
Указывает, какие записи [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) необходимо маршалировать обратно на сервер.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [маршалоптионсенум](../../../ado/reference/ado-api/marshaloptionsenum.md) . Значение по умолчанию — **адмаршалалл**.  
  
## <a name="remarks"></a>Remarks  
 При использовании [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md)на стороне клиента записи, которые были изменены на клиенте, записываются обратно на средний уровень или на веб-сервер с помощью метода, называемого упаковкой, процесс упаковки и отправки параметров метода интерфейса через границы потока или процесса. Установка свойства **MarshalOptions** может повысить производительность при передаче измененных удаленных данных для обновления на среднем уровне или на веб-сервере.  
  
> [!NOTE]
>  **Использование удаленной службы данных** Это свойство используется только в **наборе записей**на стороне клиента.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства MarshalOptions (Visual Basic)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [Пример свойства MarshalOptions (Visual C++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
