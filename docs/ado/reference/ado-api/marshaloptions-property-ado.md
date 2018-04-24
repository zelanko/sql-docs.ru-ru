---
title: Свойство MarshalOptions (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MarshalOptions
helpviewer_keywords:
- MarshalOptions property [ADO]
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5c840992cc83c3237359f40d372bfc05b1f8f21c
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="marshaloptions-property-ado"></a>Свойство MarshalOptions (ADO)
Указывает, какие записи [записей](../../../ado/reference/ado-api/recordset-object-ado.md) должны маршалироваться обратно на сервер.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md) значение. Значение по умолчанию — **adMarshalAll**.  
  
## <a name="remarks"></a>Замечания  
 При использовании на стороне клиента [записей](../../../ado/reference/ado-api/recordset-object-ado.md), записей, которые были изменены на клиентском компьютере записываются обратно на средний уровень или веб-сервер, называемый маршалинг процесс упаковки и отправки метода интерфейса Параметры за пределами границ потока или процесса. Установка **MarshalOptions** свойства может повысить производительность при маршалинге измененных удаленных данных для обновления на средний уровень или на веб-сервере.  
  
> [!NOTE]
>  **Удаленное использование службы данных** это свойство используется только на стороне клиента **записей**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства MarshalOptions (Visual Basic)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [Пример свойства MarshalOptions (Visual C++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
