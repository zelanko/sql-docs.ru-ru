---
title: Пример свойства MarshalOptions (ADO) | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: 69b9b44fc20fe832bffdd4c03536117a626916ac
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66697294"
---
# <a name="marshaloptions-property-ado"></a>Свойство MarshalOptions (ADO)
Указывает, какие записи [записей](../../../ado/reference/ado-api/recordset-object-ado.md) должны маршалироваться обратно к серверу.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md) значение. Значение по умолчанию — **adMarshalAll**.  
  
## <a name="remarks"></a>Примечания  
 При использовании клиентской стороны [записей](../../../ado/reference/ado-api/recordset-object-ado.md), записей, которые были изменены на клиенте записываются обратно в средний уровень или веб-сервера, называемый маршалинга, процесс упаковки и отправки метода интерфейса Параметры за пределами границ потока или процесса. Установка **MarshalOptions** свойства может повысить производительность при маршалинге измененный удаленных данных для обновления на среднем уровне или на веб-сервер.  
  
> [!NOTE]
>  **Удаленное использование службы данных** это свойство используется только на стороне клиента **записей**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства MarshalOptions (Visual Basic)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [Пример свойства MarshalOptions (Visual C++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
