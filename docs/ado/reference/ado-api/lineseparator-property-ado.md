---
title: Свойство LineSeparator (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76534a2925954c18d54ca7b14a3811d2544e233f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279293"
---
# <a name="lineseparator-property-ado"></a>Свойство LineSeparator (ADO)
Указывает двоичный символ для использования в качестве разделителя строк в тексте [поток](../../../ado/reference/ado-api/stream-object-ado.md) объектов.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) значение, указывающее знак разделителя строки, используемый в **поток**. Значение по умолчанию — **adCRLF**.  
  
## <a name="remarks"></a>Примечания  
 **LineSeparator** для интерпретации строк при чтении содержимого текстового **поток**. Строки могут быть пропущены с [SkipLine](../../../ado/reference/ado-api/skipline-method.md) метод.  
  
 **LineSeparator** используется только с текстом **поток** объектов ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**). Это свойство учитывается, если **тип** — **adTypeBinary**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
