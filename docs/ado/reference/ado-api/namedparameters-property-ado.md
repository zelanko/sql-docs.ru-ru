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
ms.openlocfilehash: b520f60f9e08c5580e2f825a76d25c2cdcda6ae0
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774123"
---
# <a name="namedparameters-property-ado"></a>Свойство NamedParameters (ADO)
Указывает, следует ли передавать имена параметров поставщику.  
  
## <a name="remarks"></a>Remarks  
 Если это свойство имеет значение true, ADO передает значение свойства **Name** каждого параметра в коллекции **параметров** для [объекта Command](./command-object-ado.md). Поставщик использует имя параметра для сопоставления параметров в свойствах **CommandText** или **CommandStream** . Если это свойство имеет значение false (по умолчанию), имена параметров игнорируются, а поставщик использует порядок параметров для сопоставления значений с параметрами в свойствах **CommandText** или **CommandStream** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Command (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство CommandText (ADO)](./commandtext-property-ado.md)   
 [Свойство CommandStream (ADO)](./commandstream-property-ado.md)   
 [Коллекция Parameters (ADO)](./parameters-collection-ado.md)