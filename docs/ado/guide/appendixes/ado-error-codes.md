---
description: Захват кодов ошибок ADO
title: Коды ошибок ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], error codes
ms.assetid: 3aee61c7-a9b7-4596-b78e-5828a00d0281
author: rothja
ms.author: jroth
ms.openlocfilehash: 2502e1dec35ec0d6450190650a18ac765ce14421
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88355230"
---
# <a name="capture-ado-error-codes"></a>Захват кодов ошибок ADO
В дополнение к ошибкам поставщика, возвращаемым в объектах [ошибок](../../../ado/reference/ado-api/error-object.md) коллекции [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) , объекты ADO могут возвращать ошибки механизму обработки исключений среды выполнения. Используйте механизм перехвата ошибок для языка программирования, например оператор **On Error** в Microsoft® Visual Basic, или блок **try-catch** в Microsoft Visual C++®, чтобы собрать ошибки ADO.

 Список кодов ошибок ADO см. в разделе [еррорвалуинум](../../../ado/reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>См. также:
 Коллекция ошибок [объектов Error](../../../ado/reference/ado-api/error-object.md) [(ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)
