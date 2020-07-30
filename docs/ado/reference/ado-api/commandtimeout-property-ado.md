---
title: Свойство CommandTimeout (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0b708b2b79c22240468811732d2ffae0955ea204
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242784"
---
# <a name="commandtimeout-property-ado"></a>Свойство CommandTimeout (ADO)
Указывает время ожидания при выполнении команды перед завершением попытки и генерацией ошибки.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **длинное** значение, указывающее время ожидания выполнения команды (в секундах). По умолчанию 30.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **CommandTimeout** для объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) или объекта [Command](../../../ado/reference/ado-api/command-object-ado.md) , чтобы разрешить отмену вызова метода [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-command.md) из-за задержки сетевого трафика или интенсивного использования сервера. Если интервал, заданный в свойстве **CommandTimeout** , истекает до завершения выполнения команды, возникает ошибка и ADO отменяет команду. Если присвоить свойству значение 0, то до завершения выполнения ADO будет ждать неограниченно. Убедитесь, что поставщик и источник данных, в которых пишется код, поддерживают функцию **CommandTimeout** .  
  
 Параметр **CommandTimeout** для объекта **соединения** не влияет на параметр **CommandTimeout** в объекте **Command** в том же **соединении**. то есть, свойство **CommandTimeout** объекта **команды** не наследует значение значения **CommandTimeout** объекта **соединения** .  
  
 Для объекта **соединения** свойство **CommandTimeout** остается доступен для чтения и записи после открытия **соединения** .  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual c++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Свойство ConnectionTimeout (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
