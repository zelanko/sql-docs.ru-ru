---
title: Состояние свойств (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 812863395c2980f341ed2419eee1d9d661f19dd0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822170"
---
# <a name="state-property-ado-md"></a>Свойство State (многомерные объекты ADO)
Указывает текущее состояние набора ячеек.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **Long** целое число, указывающее текущее состояние [набора ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта и доступен только для чтения. Допустимы следующие значения: **adStateClosed** (0) и **adStateOpen** (1).  
  
## <a name="remarks"></a>Примечания  
 Чтобы использовать [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) имена констант, необходимо иметь ADO библиотеки типов, на которые ссылается проект. См. в разделе [использование объектов ADO с ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md) Дополнительные сведения.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Close-метод (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Метод Open (многомерные объекты ADO)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
