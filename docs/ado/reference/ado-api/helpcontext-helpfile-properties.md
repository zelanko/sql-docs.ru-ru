---
description: Свойства HelpContext и HelpFile
title: HelpContext, свойства HelpFile | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetHelpContext
- Error::GetHelpFile
- Error::get_HelpFile
- Error::get_HelpContext
- Error::HelpContext
- Error::HelpFile
helpviewer_keywords:
- HelpContext property [ADO]
- HelpFile property [ADO]
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
author: rothja
ms.author: jroth
ms.openlocfilehash: a4d4aacd44cc6dd245026f84b826d4c007f6b696
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774873"
---
# <a name="helpcontext-helpfile-properties"></a>Свойства HelpContext и HelpFile
Указывает файл справки и раздел, связанный с объектом [Error](./error-object.md) .  
  
## <a name="return-values"></a>Возвращаемые значения  
  
-   **Хелпконтекстид** Возвращает идентификатор контекста в виде **длинного** значения для раздела в файле справки.  
  
-   **HelpFile** Возвращает **строковое** значение, результатом которого является полностью разрешенный путь к файлу справки.  
  
## <a name="remarks"></a>Remarks  
 Если в свойстве **HelpFile** указан файл справки, свойство **HelpContext** используется для автоматического вывода справочного раздела, который он идентифицирует. Если соответствующий раздел справки недоступен, свойство **HelpContext** возвращает нуль, а свойство **HelpFile** возвращает строку нулевой длины ("").  
  
## <a name="applies-to"></a>Применение  
 [Объект Error](./error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](./description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](./description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](./description-property.md)   
 [Свойство Number (ADO)](./number-property-ado.md)   
 [Свойство Source (объект Error ADO)](./source-property-ado-error.md)