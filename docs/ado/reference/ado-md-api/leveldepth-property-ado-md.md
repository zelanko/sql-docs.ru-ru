---
description: Свойство LevelDepth (многомерные объекты ADO)
title: Свойство LevelDepth (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LevelDepth
- Member::LevelDepth
helpviewer_keywords:
- LevelDepth property [ADO MD]
ms.assetid: 8a1cfe2c-f207-4445-b152-ade090f64608
author: rothja
ms.author: jroth
ms.openlocfilehash: 2c21b038df300a5c941d01ba65fdc7240d55c32f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986495"
---
# <a name="leveldepth-property-ado-md"></a>Свойство LevelDepth (многомерные объекты ADO)
Указывает количество уровней между корневым элементом иерархии и [элементом](./member-object-ado-md.md).  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинное** целое число и доступно только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Свойство **LevelDepth** используется для определения расстояния от объекта [member](./member-object-ado-md.md)на корневом уровне иерархии. **LevelDepth**элемента на корневом уровне равен 0. Это соответствует свойству [Depth](./depth-property-ado-md.md) объекта [Level](./level-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Member (многомерные объекты ADO)](./member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Depth (объекты данных ActiveX (MD))](./depth-property-ado-md.md)   
 [Объект Level (многомерные объекты ADO)](./level-object-ado-md.md)