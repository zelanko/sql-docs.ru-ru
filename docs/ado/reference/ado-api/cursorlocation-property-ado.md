---
description: Свойство CursorLocation (ADO)
title: Свойство CursorLocation (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
author: rothja
ms.author: jroth
ms.openlocfilehash: 92567057acad1edb0a0571a0057a11a47a3c65d6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444306"
---
# <a name="cursorlocation-property-ado"></a>Свойство CursorLocation (ADO)
Указывает расположение службы курсора.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , которое можно задать для одного из значений [курсорлокатионенум](../../../ado/reference/ado-api/cursorlocationenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Это свойство позволяет выбрать между различными библиотеками курсоров, доступными для поставщика. Обычно можно выбрать одну из них, используя библиотеку курсоров на стороне клиента или ту, которая находится на сервере.  
  
 Этот параметр свойства влияет на соединения, установленные только после установки свойства. Изменение свойства **CursorLocation** не влияет на существующие соединения.  
  
 Курсоры, возвращаемые методом [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-connection.md) , наследуют этот параметр. Объекты **набора записей** будут автоматически наследовать этот параметр от связанных соединений.  
  
 Это свойство доступно для чтения и записи в [соединении](../../../ado/reference/ado-api/connection-object-ado.md) или закрытом [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md)и доступно только для чтения в открытом **наборе записей**.  
  
> [!NOTE]
>  **Использование удаленной службы данных** При использовании **набора записей** или объекта **соединения** на стороне клиента свойство **CursorLocation** может иметь только значение **адусеклиент**.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
