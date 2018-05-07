---
title: Объект параметра | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameter
helpviewer_keywords:
- Parameter object [ADO]
ms.assetid: e010e794-7f0f-4026-8b5b-37328e437d63
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59474a000d3def675caf66085380c6a3791805c3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="parameter-object"></a>Объект Parameter
Представляет параметр или аргумент, связанный с [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, основанного на параметризованный запрос или хранимую процедуру.  
  
## <a name="remarks"></a>Замечания  
 Многие поставщики поддерживают параметризованные команды. Это команды, в которых нужное действие определяется один раз, но переменные (или параметров) используются для изменения некоторые сведения о команды. Например инструкцию SQL SELECT использовать параметр для определения условия соответствия предложение WHERE, а другой для определения имени столбца для СОРТИРОВКИ BY.  
  
 **Параметр** объекты представляют параметры, связанные с параметризованными запросами или ввода-вывода аргументов и возвращаемых значений из хранимых процедур. В зависимости от функциональности поставщик некоторых коллекций, методы и свойства **параметр** могут оказаться недоступными.  
  
 С коллекциями, методы и свойства **параметр** объекта, можно сделать следующее:  
  
-   Задание или возврат имя параметра с [имя](../../../ado/reference/ado-api/name-property-ado.md) свойства.  
  
-   Задание или возврат значения параметра с [значение](../../../ado/reference/ado-api/value-property-ado.md) свойства. **Значение** — свойство по умолчанию **параметр** объекта.  
  
-   Задание или возврат характеристики параметров с [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md), [направление](../../../ado/reference/ado-api/direction-property.md), [точности](../../../ado/reference/ado-api/precision-property-ado.md), [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md), [ Размер](../../../ado/reference/ado-api/size-property-ado-parameter.md), и [тип](../../../ado/reference/ado-api/type-property-ado.md) свойства.  
  
-   Передайте долго двоичных или символьных данных для параметра с [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) метод.  
  
-   Доступ к атрибуты поставщика, с помощью [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 Если вам известны имена и свойства параметров, связанных с хранимой процедуры или параметризованного запроса необходимо вызвать, можно использовать [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) метод для создания **параметр** объектов с соответствующими параметрами свойств, а также с помощью [Append](../../../ado/reference/ado-api/append-method-ado.md) метод, чтобы добавить их к [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции. Это позволяет задать и возвращают значения параметров без вызова [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод **параметры** коллекции для получения сведений о параметрах от поставщика, потенциально — ресурсоемкая операция.  
  
 **Параметр** объект не является безопасным для создания сценариев.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Параметр объекта свойства, методы и события](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект команды (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Коллекция параметров (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
