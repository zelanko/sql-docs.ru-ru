---
description: Объект Parameter
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
author: rothja
ms.author: jroth
ms.openlocfilehash: eac5abf388644cff05c4a3a81955f025c65dd7aa
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773413"
---
# <a name="parameter-object"></a>Объект Parameter
Представляет параметр или аргумент, связанный с объектом [Command](./command-object-ado.md) на основе параметризованного запроса или хранимой процедуры.  
  
## <a name="remarks"></a>Remarks  
 Многие поставщики поддерживают параметризованные команды. Это команды, в которых нужное действие определено один раз, но переменные (или параметры) используются для изменения некоторых сведений о команде. Например, инструкция SQL SELECT может использовать параметр для определения критерия сопоставления предложения WHERE, а другой — для определения имени столбца для предложения сортировки по.  
  
 Объекты **параметров** представляют параметры, связанные с параметризованными запросами, а также входные и выходные аргументы и возвращаемые значения хранимых процедур. В зависимости от функциональных возможностей поставщика некоторые коллекции, методы или свойства объекта **параметров** могут быть недоступны.  
  
 С помощью коллекций, методов и свойств объекта **Parameter** можно выполнять следующие действия.  
  
-   Задайте или верните имя параметра с помощью свойства [Name](./name-property-ado.md) .  
  
-   Задайте или верните значение параметра со свойством [value](./value-property-ado.md) . **Значение** является свойством по умолчанию для объекта **Parameter** .  
  
-   Установка или возврат характеристик параметров с помощью свойств [Attributes](./attributes-property-ado.md), [Direction](./direction-property.md), [Precision](./precision-property-ado.md), [NumericScale](./numericscale-property-ado.md), [size](./size-property-ado-parameter.md)и [Type](./type-property-ado.md) .  
  
-   Передайте длинные двоичные или символьные данные в параметр с помощью метода [AppendChunk](./appendchunk-method-ado.md) .  
  
-   Доступ к атрибутам, зависящим от поставщика, с помощью коллекции [Properties](./properties-collection-ado.md) .  
  
 Если вы знакомы с именами и свойствами параметров, связанных с хранимой процедурой или параметризованным запросом, который необходимо вызвать, можно использовать метод [CreateParameter](./createparameter-method-ado.md) для создания объектов **параметров** с соответствующими параметрами свойств и использовать метод [append](./append-method-ado.md) для их добавления в коллекцию [Parameters](./parameters-collection-ado.md) . Это позволяет задавать и возвращать значения параметров без вызова метода [Refresh](./refresh-method-ado.md) в коллекции **Parameters** для получения сведений о параметрах от поставщика, потенциально требовательных к ресурсам операций.  
  
 Объект **параметра** не является надежным для скриптов.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Parameter](./parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Command (ADO)](./command-object-ado.md)   
 [Метод CreateParameter (ADO)](./createparameter-method-ado.md)   
 [Коллекция Parameters (ADO)](./parameters-collection-ado.md)   
 [Коллекция Properties (ADO)](./properties-collection-ado.md)