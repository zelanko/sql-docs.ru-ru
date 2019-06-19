---
title: Свойство (объект Parameter ADO) Size | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Size
helpviewer_keywords:
- Size property [ADO Parameter]
ms.assetid: e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: caad25759038fde0107fa7602394de2a8a01e38c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711495"
---
# <a name="size-property-ado-parameter"></a>Свойство Size (объект Parameter ADO)
Указывает максимальный размер, в байты или символы, из [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Long** значение, указывающее максимальный размер в байты или символы значения в **параметр** объекта.  
  
## <a name="remarks"></a>Примечания  
 Используйте **размер** определить максимальный размер для значения, записи или чтения из свойства [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство **параметр** объекта.  
  
 Если вы укажите тип данных переменной длины для **параметр** объекта (например, любой **строка** тип, например **adVarChar**), нужно задать объект  **Размер** свойство перед добавлением его в [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции; в противном случае возникает ошибка.  
  
 Если уже добавленные **параметр** объект **параметры** коллекцию [команда](../../../ado/reference/ado-api/command-object-ado.md) объект и изменить его тип с типом данных переменной длины, вам необходимо Задайте **параметр** объекта **размер** свойство перед выполнением **команда** объект; в противном случае возникает ошибка.  
  
 Если вы используете [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод, чтобы получить сведения о параметрах от поставщика и он возвращает тип данных переменной длины, один или несколько **параметр** объектов ADO может выделить память для параметров, на основе на их максимальный потенциальный размер, что может вызвать ошибку во время выполнения. Чтобы предотвратить ошибку, необходимо явно указать **размер** свойства для этих параметров перед выполнением команды.  
  
 **Размер** свойство доступно для чтения/записи.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>См. также  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление свойства пример (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление пример свойства (Visual C++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление примеры свойств (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Свойство Size (объект Stream ADO)](../../../ado/reference/ado-api/size-property-ado-stream.md)
