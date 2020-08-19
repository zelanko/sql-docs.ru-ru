---
description: Свойство Direction
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 37987e58829b1b6957b4fe1de440aaeb4aae1763
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444056"
---
# <a name="direction-property"></a>Свойство Direction
Указывает, представляет ли [параметр](../../../ado/reference/ado-api/parameter-object.md) входной параметр, выходной параметр, входной и выходной параметры, или значение, если параметр является возвращаемым значением хранимой процедуры.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [параметердиректионенум](../../../ado/reference/ado-api/parameterdirectionenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Свойство **Direction** используется для указания способа передачи параметра в процедуру или из процедуры. Свойство **Direction** доступно для чтения и записи; Это позволяет работать с поставщиками, которые не возвращают эту информацию, или задавать эту информацию, если вы не хотите, чтобы ADO вызывал дополнительный вызов поставщика для получения сведений о параметрах.  
  
 Не все поставщики могут определить направление параметров в хранимых процедурах. В таких случаях необходимо задать свойство **Direction** перед выполнением запроса.  
  
## <a name="applies-to"></a>Применение  
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual c++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
