---
title: Свойство Direction | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Direction
helpviewer_keywords:
- Direction property
ms.assetid: d5732578-3434-4dcd-a9f7-db1abd1b3b94
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df2f7cc5eadce7d4f8f61674f4915ec3b1561e02
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63180961"
---
# <a name="direction-property"></a>Свойство Direction
Указывает ли [параметр](../../../ado/reference/ado-api/parameter-object.md) представляет входного параметра, выходного параметра, входной и выходной параметр, или если параметр является возвращаемым значением из хранимой процедуры.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) значение.  
  
## <a name="remarks"></a>Примечания  
 Используйте **направление** свойство, чтобы указать, каким образом параметр передается в или из процедуры. **Направление** свойство доступно для чтения/записи; это позволяет для работы с поставщиками, которые не возвращают эти сведения или установить эту информацию в том случае, если вы не хотите ADO для выполнения дополнительного вызова к поставщику для получения сведений о параметрах.  
  
 Не все поставщики можно определить направление параметров в хранимых процедур. В таком случае необходимо задать **направление** свойство перед выполнением запроса.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>См. также  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление свойства пример (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление пример свойства (Visual C++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление примеры свойств (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
