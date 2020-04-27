---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ba441a52958e423308e648f15dd36e14d6d1d895
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918470"
---
# <a name="helpcontext-helpfile-properties"></a>Свойства HelpContext и HelpFile
Указывает файл справки и раздел, связанный с объектом [Error](../../../ado/reference/ado-api/error-object.md) .  
  
## <a name="return-values"></a>Возвращаемые значения  
  
-   **Хелпконтекстид** Возвращает идентификатор контекста в виде **длинного** значения для раздела в файле справки.  
  
-   **HelpFile** Возвращает **строковое** значение, результатом которого является полностью разрешенный путь к файлу справки.  
  
## <a name="remarks"></a>Remarks  
 Если в свойстве **HelpFile** указан файл справки, свойство **HelpContext** используется для автоматического вывода справочного раздела, который он идентифицирует. Если соответствующий раздел справки недоступен, свойство **HelpContext** возвращает нуль, а свойство **HelpFile** возвращает строку нулевой длины ("").  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](../../../ado/reference/ado-api/description-property.md)   
 [Свойство Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Свойство Source (объект Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
