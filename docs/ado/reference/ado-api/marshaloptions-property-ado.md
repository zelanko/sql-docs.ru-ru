---
description: Свойство MarshalOptions (ADO)
title: Свойство MarshalOptions (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e7e574836f09df6f3bb8fdb078661c85cbf6355
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990675"
---
# <a name="marshaloptions-property-ado"></a>Свойство MarshalOptions (ADO)
Указывает, какие записи [набора записей](./recordset-object-ado.md) необходимо маршалировать обратно на сервер.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [маршалоптионсенум](./marshaloptionsenum.md) . Значение по умолчанию — **адмаршалалл**.  
  
## <a name="remarks"></a>Remarks  
 При использовании [набора записей](./recordset-object-ado.md)на стороне клиента записи, которые были изменены на клиенте, записываются обратно на средний уровень или на веб-сервер с помощью метода, называемого упаковкой, процесс упаковки и отправки параметров метода интерфейса через границы потока или процесса. Установка свойства **MarshalOptions** может повысить производительность при передаче измененных удаленных данных для обновления на среднем уровне или на веб-сервере.  
  
> [!NOTE]
>  **Использование удаленной службы данных** Это свойство используется только в **наборе записей**на стороне клиента.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства MarshalOptions (Visual Basic)](./marshaloptions-property-example-vb.md)   
 [Пример свойства MarshalOptions (Visual C++)](./marshaloptions-property-example-vc.md)