---
description: Захват кодов ошибок ADO
title: Коды ошибок ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], error codes
ms.assetid: 3aee61c7-a9b7-4596-b78e-5828a00d0281
author: rothja
ms.author: jroth
ms.openlocfilehash: aa933f7be33f564af3aaf2851f6ec32bd5b4c5d4
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991185"
---
# <a name="capture-ado-error-codes"></a>Захват кодов ошибок ADO
В дополнение к ошибкам поставщика, возвращаемым в объектах [ошибок](../../reference/ado-api/error-object.md) коллекции [Errors](../../reference/ado-api/errors-collection-ado.md) , объекты ADO могут возвращать ошибки механизму обработки исключений среды выполнения. Используйте механизм перехвата ошибок для языка программирования, например оператор **On Error** в Microsoft® Visual Basic, или блок **try-catch** в Microsoft Visual C++®, чтобы собрать ошибки ADO.

 Список кодов ошибок ADO см. в разделе [еррорвалуинум](../../reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>См. также
 Коллекция ошибок [объектов Error](../../reference/ado-api/error-object.md) [(ADO)](../../reference/ado-api/errors-collection-ado.md)