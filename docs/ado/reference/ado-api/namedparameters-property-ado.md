---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ce517f4ba3f2fc4a80932024a8fe51ac285cdb7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707295"
---
# <a name="namedparameters-property-ado"></a>Свойство NamedParameters (ADO)
Указывает, следует ли передавать имена параметров к поставщику.  
  
## <a name="remarks"></a>Примечания  
 Если это свойство имеет значение true, ADO передает значение **имя** свойства каждого параметра в **параметр** коллекции для [объект команды](../../../ado/reference/ado-api/command-object-ado.md). Поставщик использует имя параметра, чтобы соответствовать параметрам в **CommandText** или **CommandStream** свойства. Если это свойство имеет значение false (по умолчанию), имена параметров пропускаются, и поставщик использует порядок параметров для сопоставления значений для параметров в **CommandText** или **CommandStream** свойства.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Свойство CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
