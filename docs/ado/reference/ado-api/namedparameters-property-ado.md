---
description: Свойство NamedParameters (ADO)
title: Свойство NamedParameters (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 18552a7d15a5dbe36a05c7391d0fd7e2ab3a6d94
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990495"
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