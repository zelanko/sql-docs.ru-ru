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
manager: jroth
ms.openlocfilehash: 152186c0bb1c2fb75197a920e06e0b6bb96dadd0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703318"
---
# <a name="parameter-object"></a>Объект Parameter
Представляет параметр или аргумент, связанный с [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта на основании параметризованного запроса или хранимой процедуры.  
  
## <a name="remarks"></a>Примечания  
 Многие поставщики поддерживают параметризованные команды. Ниже приведены команды, в которых нужное действие определяется один раз, но переменные (или параметров) используются для изменения некоторые дополнительные сведения о команде. Например инструкцию SQL SELECT использовать параметр для определения условий соответствия предложение WHERE, и другой, чтобы определить имя столбца для СОРТИРОВКИ BY.  
  
 **Параметр** объекты представляют параметры, связанные с параметризованными запросами или входные/выходные аргументы и возвращаемые значения для хранимых процедур. В зависимости от того, функциональные возможности поставщика, некоторые коллекции, методы или свойства **параметр** могут оказаться недоступными.  
  
 С помощью коллекций, методы и свойства **параметр** объекта, можно сделать следующее:  
  
-   Задает или возвращает имя параметра с [имя](../../../ado/reference/ado-api/name-property-ado.md) свойство.  
  
-   Задание или возврат значения параметра с [значение](../../../ado/reference/ado-api/value-property-ado.md) свойства. **Значение** — свойство по умолчанию **параметр** объекта.  
  
-   Задание или возврат характеристики параметров с [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md), [направление](../../../ado/reference/ado-api/direction-property.md), [точности](../../../ado/reference/ado-api/precision-property-ado.md), [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md), [ Размер](../../../ado/reference/ado-api/size-property-ado-parameter.md), и [тип](../../../ado/reference/ado-api/type-property-ado.md) свойства.  
  
-   Передайте долго двоичных или символьных данных для параметра с [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) метод.  
  
-   Доступ к особые атрибуты поставщика, используя [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 Если вы знаете имена и свойства параметров, связанные с помощью хранимой процедуры или параметризированного запроса необходимо вызвать, можно использовать [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) метод для создания **параметр** объектов с соответствующими параметрами свойств и используйте [Append](../../../ado/reference/ado-api/append-method-ado.md) метод, чтобы добавить их в [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции. Это позволяет задать и получить значения параметров не нужно звонить [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод **параметры** коллекции для получения сведений о параметрах от поставщика, потенциально — ресурсоемкая операция.  
  
 **Параметр** объект не является безопасным для использования в сценариях.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Параметр свойства объекта, методы и события](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
