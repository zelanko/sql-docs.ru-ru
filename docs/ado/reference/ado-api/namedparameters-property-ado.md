---
description: Свойство NamedParameters (ADO)
title: Свойство NamedParameters (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
author: rothja
ms.author: jroth
ms.openlocfilehash: ff11a0f5211c0f77ccd36b58ea6b8a5699a390cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443186"
---
# <a name="namedparameters-property-ado"></a>Свойство NamedParameters (ADO)
Указывает, следует ли передавать имена параметров поставщику.  
  
## <a name="remarks"></a>Remarks  
 Если это свойство имеет значение true, ADO передает значение свойства **Name** каждого параметра в коллекции **параметров** для [объекта Command](../../../ado/reference/ado-api/command-object-ado.md). Поставщик использует имя параметра для сопоставления параметров в свойствах **CommandText** или **CommandStream** . Если это свойство имеет значение false (по умолчанию), имена параметров игнорируются, а поставщик использует порядок параметров для сопоставления значений с параметрами в свойствах **CommandText** или **CommandStream** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Свойство CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
