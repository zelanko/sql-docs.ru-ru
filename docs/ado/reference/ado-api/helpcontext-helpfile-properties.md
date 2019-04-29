---
title: HelpContext, HelpFile свойства | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 059bb0e945875d36582d08f8018bad485475639d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027978"
---
# <a name="helpcontext-helpfile-properties"></a>Свойства HelpContext и HelpFile
Указывает файл справки и раздел, связанный с [ошибка](../../../ado/reference/ado-api/error-object.md) объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
  
-   **Идентификатор справки** возвращает идентификатор контекста, в виде **Long** значение для раздела в файле справки.  
  
-   **HelpFile** возвращает **строка** значению, которое возвращает полностью разрешенной путь к файлу справки.  
  
## <a name="remarks"></a>Примечания  
 Если указан файл справки в **HelpFile** свойство, **HelpContext** свойство используется для автоматического отображения раздела справки идентифицирует его. Если имеется соответствующий раздел справки отсутствует, **HelpContext** свойство возвращает ноль и **HelpFile** свойство возвращает строку нулевой длины (»»).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Description, HelpContext, HelpFile, NativeError, номер, источника и SQLState свойства пример (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, HelpFile, NativeError, номер, источника и пример свойства SQLState (Visual C++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](../../../ado/reference/ado-api/description-property.md)   
 [Свойство Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Свойство Source (объект Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
