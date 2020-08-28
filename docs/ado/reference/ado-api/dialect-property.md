---
description: Свойство Dialect
title: Свойство диалекта | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
author: rothja
ms.author: jroth
ms.openlocfilehash: be93ceb76aa0aadba5b28673c16704b0881186f9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973905"
---
# <a name="dialect-property"></a>Свойство Dialect
Указывает диалект свойств [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) или [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) . Диалект определяет синтаксис и общие правила, которые поставщик использует для анализа строки или потока.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Свойство **диалекта** содержит допустимый идентификатор GUID, представляющий диалект текста команды или потока. Значение этого свойства по умолчанию — {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}, которое указывает, что поставщик должен выбрать способ интерпретации текста команды или потока.  
  
## <a name="remarks"></a>Remarks  
 ADO не выполняет запрос к поставщику, когда пользователь считывает значение этого свойства; Он возвращает строковое представление значения, хранящегося в объекте [Command](../../../ado/reference/ado-api/command-object-ado.md) в данный момент.  
  
 Когда пользователь задает свойство **диалекта** , ADO проверяет GUID и выдает ошибку, если переданное значение не является ДОПУСТИМЫм идентификатором GUID. См. документацию для поставщика, чтобы определить значения GUID, поддерживаемые свойством **диалекта** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Execute (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)
