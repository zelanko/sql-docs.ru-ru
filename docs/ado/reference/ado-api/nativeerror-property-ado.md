---
title: Свойство NativeError (ADO) | Документы Microsoft
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
- Error::GetNativeError
- Error::get_NativeError
- Error::NativeError
helpviewer_keywords:
- NativeError property [ADO]
ms.assetid: b9b47e57-18a4-4186-aef5-5bd18d7b1d74
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3dd8b2962e460606da23ac207daa0e5e2ad3d465
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="nativeerror-property-ado"></a>Свойство NativeError (ADO)
Указывает код ошибки поставщика для данного [ошибка](../../../ado/reference/ado-api/error-object.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **длинные** значение, указывающее код ошибки.  
  
## <a name="remarks"></a>Замечания  
 Используйте **NativeError** свойства, чтобы получить сведения об ошибке в конкретной базе данных для какого-либо **ошибка** объекта. Например, при использовании поставщика Microsoft ODBC для OLE DB с базой данных Microsoft SQL Server, коды собственных ошибок, возникших в SQL Server проходить через ODBC и поставщик ODBC ADO **NativeError** свойство.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Описание, HelpContext, файл справки, NativeError, номер, источника и пример свойства SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, файл справки, NativeError, номер, источник и пример свойства SQLState (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
