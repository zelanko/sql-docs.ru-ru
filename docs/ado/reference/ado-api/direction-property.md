---
title: "Свойство Direction | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::Direction
helpviewer_keywords:
- Direction property
ms.assetid: d5732578-3434-4dcd-a9f7-db1abd1b3b94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a81c60a4505e1c5e420583c474109d0d08f4fb6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="direction-property"></a>Свойство Direction
Указывает, является ли [параметр](../../../ado/reference/ado-api/parameter-object.md) представляет входного параметра, выходного параметра, входного и выходного параметра, или если параметр имеет значение, возвращаемое хранимой процедуры.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) значение.  
  
## <a name="remarks"></a>Замечания  
 Используйте **направление** свойство, чтобы указать, каким образом параметр передается в или из процедуры. **Направление** свойство является чтение и запись; это позволяет для работы с поставщиками, которые не возвращают эти сведения или установить эту информацию, если вы не хотите ADO, чтобы сделать дополнительного обращения к поставщику для получения сведений о параметрах.  
  
 Не все поставщики можно определить направление параметров в хранимых процедур. В этих случаях необходимо установить **направление** свойство перед выполнением запроса.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект параметра](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>См. также:  
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление примере свойства (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)

