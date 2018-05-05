---
title: Свойство Dialect | Документы Microsoft
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
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74299cc953c3ac94653860d18d0ee7774ecf49ad
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="dialect-property"></a>Свойство Dialect
Указывает, диалект [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) или [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) свойства. Диалект определяет синтаксис и общие правила, поставщик использует для синтаксического анализа в строку или поток.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 **Диалект** свойство содержит допустимый идентификатор GUID, который представляет разновидность текст команды или поток. Значение по умолчанию для этого свойства — {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}, указывающая, что поставщик следует выбирать способ интерпретации текста команды или поток.  
  
## <a name="remarks"></a>Замечания  
 ADO не запрашивает поставщика, когда пользователь считывает значение этого свойства. Возвращает строковое представление значения, хранящегося в [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта.  
  
 Когда пользователь задает **диалект** свойство ADO проверяет идентификатор GUID и вызывает ошибку, если указанное значение не является допустимым идентификатором GUID. См. в документации к поставщику для определения значения идентификатора GUID, поддерживаемые **диалект** свойство.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Execute (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)
