---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afee71d4f37e2b3a27247fbeacf51dab66cc1e23
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933288"
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
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также:  
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
