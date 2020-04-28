---
title: Объект Parameter | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameter
helpviewer_keywords:
- Parameter object [ADO]
ms.assetid: e010e794-7f0f-4026-8b5b-37328e437d63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15df27e3dc48decf743a78dd4d147a22dc7cf276
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931665"
---
# <a name="parameter-object"></a>Объект Parameter
Представляет параметр или аргумент, связанный с объектом [Command](../../../ado/reference/ado-api/command-object-ado.md) на основе параметризованного запроса или хранимой процедуры.  
  
## <a name="remarks"></a>Remarks  
 Многие поставщики поддерживают параметризованные команды. Это команды, в которых нужное действие определено один раз, но переменные (или параметры) используются для изменения некоторых сведений о команде. Например, инструкция SQL SELECT может использовать параметр для определения критерия сопоставления предложения WHERE, а другой — для определения имени столбца для предложения сортировки по.  
  
 Объекты **параметров** представляют параметры, связанные с параметризованными запросами, а также входные и выходные аргументы и возвращаемые значения хранимых процедур. В зависимости от функциональных возможностей поставщика некоторые коллекции, методы или свойства объекта **параметров** могут быть недоступны.  
  
 С помощью коллекций, методов и свойств объекта **Parameter** можно выполнять следующие действия.  
  
-   Задайте или верните имя параметра с помощью свойства [Name](../../../ado/reference/ado-api/name-property-ado.md) .  
  
-   Задайте или верните значение параметра со свойством [value](../../../ado/reference/ado-api/value-property-ado.md) . **Значение** является свойством по умолчанию для объекта **Parameter** .  
  
-   Установка или возврат характеристик параметров с помощью свойств [Attributes](../../../ado/reference/ado-api/attributes-property-ado.md), [Direction](../../../ado/reference/ado-api/direction-property.md), [Precision](../../../ado/reference/ado-api/precision-property-ado.md), [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md), [size](../../../ado/reference/ado-api/size-property-ado-parameter.md)и [Type](../../../ado/reference/ado-api/type-property-ado.md) .  
  
-   Передайте длинные двоичные или символьные данные в параметр с помощью метода [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) .  
  
-   Доступ к атрибутам, зависящим от поставщика, с помощью коллекции [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
 Если вы знакомы с именами и свойствами параметров, связанных с хранимой процедурой или параметризованным запросом, который необходимо вызвать, можно использовать метод [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) для создания объектов **параметров** с соответствующими параметрами свойств и использовать метод [append](../../../ado/reference/ado-api/append-method-ado.md) для их добавления в коллекцию [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) . Это позволяет задавать и возвращать значения параметров без вызова метода [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) в коллекции **Parameters** для получения сведений о параметрах от поставщика, потенциально требовательных к ресурсам операций.  
  
 Объект **параметра** не является надежным для скриптов.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Parameter](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
