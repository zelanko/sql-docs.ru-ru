---
description: Свойство State (многомерные объекты ADO)
title: Свойство State (объекты данных ActiveX (MD)) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: efc3b140b2864aec7151e1235010c4a14b0b3a64
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777863"
---
# <a name="state-property-ado-md"></a>Свойство State (многомерные объекты ADO)
Указывает текущее состояние набора ячеек.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинное** целое число, указывающее текущее условие объекта набора [ячеек](./cellset-object-ado-md.md) и доступно только для чтения. Допустимы следующие значения: **адстатеклосед** (0) и **адстатеопен** (1).  
  
## <a name="remarks"></a>Remarks  
 Чтобы использовать имена констант [обжектстатинум](../ado-api/objectstateenum.md) , необходимо, чтобы в проекте была ссылка на БИБЛИОТЕКУ типов ADO. Дополнительные сведения см. в разделе [Использование ADO с объекты данных ActiveX (MD)](../../guide/multidimensional/using-ado-with-ado-md.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Cellset (многомерные объекты ADO)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Close (объекты данных ActiveX (MD))](./close-method-ado-md.md)   
 [Метод Open (многомерные объекты ADO)](./open-method-ado-md.md)