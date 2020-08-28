---
description: Свойство State (многомерные объекты ADO)
title: Свойство State (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 78b96e242cc27d27326d97f51cf378d9c5cbb51e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985985"
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