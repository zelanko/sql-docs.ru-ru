---
title: Метод Close (объекты данных ActiveX (MD)) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a0c2b9236ba60902fe53727be722723e7138aba0
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764385"
---
# <a name="close-method-ado-md"></a>Метод Close (многомерные объекты ADO)
Закрывает открытый набор ячеек.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Примечания  
 Использование метода **Close** для закрытия объекта набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) приведет к освобождению связанных данных, включая данные во всех связанных [ячейках](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [осях](../../../ado/reference/ado-md-api/axis-object-ado-md.md), [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)координатах или объектах- [элементах](../../../ado/reference/ado-md-api/member-object-ado-md.md) . Закрытие набора **ячеек** не приводит к его удалению из памяти. можно изменить параметры свойств и открыть его позже. Чтобы полностью исключить объект из памяти, присвойте переменной объекта значение **Nothing**.  
  
 Позже можно вызвать метод [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) , чтобы повторно открыть набор **ячеек** с помощью той же или другой исходной строки. Пока объект набора **ячеек** закрыт, получение любых свойств или вызов методов, ссылающихся на базовые данные или метаданные, выдает ошибку.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Axis (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Объект Cell (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Объект Member (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Метод Open (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [Объект «позиционирование» (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [Свойство State (многомерные объекты ADO)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
