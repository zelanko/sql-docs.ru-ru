---
title: Метод (многомерные Объекты ADO) Close | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Close
- Cellset::Close
helpviewer_keywords:
- Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 09e83fd8645a5c0ab604a640478c4cced4870742
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949815"
---
# <a name="close-method-ado-md"></a>Метод Close (многомерные объекты ADO)
Закрывает откройте набор ячеек.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Примечания  
 С помощью **закрыть** метод для закрытия [набора ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объект выпустит связанные данные, включая данные в любом связанные [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md), [Позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md), или [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объектов. Закрытие **набора ячеек** не удаляет его из памяти; можно изменить его параметры свойств и открыть его позже. Чтобы полностью исключить объект из памяти, присвоить переменной объекта **ничего не**.  
  
 Позже можно вызвать [откройте](../../../ado/reference/ado-md-api/open-method-ado-md.md) метод, чтобы снова открыть **набора ячеек** с помощью той же или другой строку с источником. Хотя **набора ячеек** объект был закрыт, получение всех свойств или вызова методов, которые ссылаются на базовые данные или метаданные приводит к ошибке.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Axis (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Объект Cell (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Объект-член (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Метод Open (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [Объект position (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [Свойство State (многомерные объекты ADO)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
