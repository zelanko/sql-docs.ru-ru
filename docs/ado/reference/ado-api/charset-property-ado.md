---
title: Свойство CharSet (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Charset
helpviewer_keywords:
- Charset property [ADO]
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69d65a5330ea83b955629cd9de9684ecc47906ec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920080"
---
# <a name="charset-property-ado"></a>Свойство Charset (ADO)
Указывает кодировку, в которой содержимое текстового [Stream](../../../ado/reference/ado-api/stream-object-ado.md) преобразования для хранения в внутренний буфер **Stream** объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** которого присвоено значение, указывающее знак содержимое **Stream** будет преобразован. Значение по умолчанию — **Юникода**. Допустимые значения: типичный строк, передаваемых через интерфейс, как Internet имена набора символов (например, «iso-8859-1», «Windows-1252"и т. д.). Список имен набора символов, которые заведомо системой см. в разделе подразделы HKEY_CLASSES_ROOT\MIME\Database\Charset в реестре Windows.  
  
## <a name="remarks"></a>Примечания  
 В текстовом **Stream** объект текстовые данные хранятся в кодировку, указанную с **Charset** свойство. По умолчанию используется Юникод. **Charset** свойство используется для преобразования данных, поступающих на **Stream** или ближайшие из **Stream**. Например если **Stream** содержит данные ISO-8859-1, и что данные копируются на строку BSTR, **Stream** объект преобразует данные в Юникод. То же самое будет наблюдаться и в обратной ситуации.  
  
 Для открытого **Stream**, текущий [позиции](../../../ado/reference/ado-api/position-property-ado.md) должно быть в начале **Stream** (0), чтобы обозначить **Charset**.  
  
 **CharSet** используется только с текстом **Stream** объектов ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**). Это свойство учитывается, если **тип** — **adTypeBinary**.  
  
 Пример кода, см. в разделе [Step 4: Заполнение текстового поля сведений](../../../ado/guide/data/step-4-populate-the-details-text-box.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
