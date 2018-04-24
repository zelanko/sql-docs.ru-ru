---
title: Свойство электрической ПЕРЕГРУЗКИ | Документы Microsoft
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
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a611caa546cb80004cccf7664b0cfe6b74078f28
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="eos-property"></a>Свойство электрической ПЕРЕГРУЗКИ
Указывает, является ли текущая позиция в конце [поток](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **логическое** значение, указывающее, является ли текущая позиция в конце потока. **Электрической ПЕРЕГРУЗКИ** возвращает **True** при наличии не большее число байтов в потоке, она возвращает **False** при наличии нескольких байтов после текущего положения.  
  
 Чтобы обозначить конец позиции в потоке, используйте [SetEOS](../../../ado/reference/ado-api/seteos-method.md) метод. Чтобы определить текущую позицию, используйте [позиции](../../../ado/reference/ado-api/position-property-ado.md) свойство.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Электрической ПЕРЕГРУЗКИ LineSeparator свойства и пример метода SkipLine (Visual Basic)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
