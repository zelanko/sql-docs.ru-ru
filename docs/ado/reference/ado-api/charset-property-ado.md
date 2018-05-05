---
title: Свойство CharSet (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Charset
helpviewer_keywords:
- Charset property [ADO]
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 972f090d648c94c3fab20f013eaa185fe3849f00
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="charset-property-ado"></a>Свойство CharSet (ADO)
Указывает кодировку, в которой содержимое текстового [поток](../../../ado/reference/ado-api/stream-object-ado.md) преобразования для хранения в внутренний буфер **поток** объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** которого присвоено значение, указывающее знак содержимое **поток** будут преобразованы. Значение по умолчанию — **Юникода**. Допустимые значения: типичные строк, передаваемых через интерфейс как Интернет имена наборов символов (например, «iso-8859-1», «Windows-1252"и т. д). Список имен набор символов, которые заведомо системой см. подраздел HKEY_CLASSES_ROOT\MIME\Database\Charset в реестре Windows.  
  
## <a name="remarks"></a>Замечания  
 В текстовом **поток** объект текстовые данные хранятся в набор знаков, указанных в **Charset** свойство. Значение по умолчанию — Unicode. **Charset** свойство используется для преобразования данных, поступающих на **поток** или ближайшие из **поток**. Например если **поток** содержит данные ISO-8859-1, и что данные копируются в тип BSTR, **поток** объекта будет преобразовать данные в Юникоде. То же самое будет наблюдаться и в обратной ситуации.  
  
 Для открытого **поток**, текущий [позиции](../../../ado/reference/ado-api/position-property-ado.md) должно быть в начале **поток** (0), чтобы можно было задать **Charset**.  
  
 **CharSet** используется только с текстом **поток** объектов ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**). Это свойство учитывается, если **тип** — **adTypeBinary**.  
  
 Пример кода см. в разделе [шаг 4: заполнить текстовое поле сведений](../../../ado/guide/data/step-4-populate-the-details-text-box.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
