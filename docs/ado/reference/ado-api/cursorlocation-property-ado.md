---
title: Свойство CursorLocation (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4ef22aa0aa82071367e9912c31f747cacf7e5075
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="cursorlocation-property-ado"></a>Свойство CursorLocation (ADO)
Указывает расположение службы курсора.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, которое может быть присвоено одно из [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) значения.  
  
## <a name="remarks"></a>Замечания  
 Это свойство позволяет выбирать различные библиотеки курсоров, доступ к поставщику. Как правило можно выбрать с помощью библиотеки курсор на стороне клиента, либо, расположенный на сервере.  
  
 Значение этого свойства влияет на соединения установлены только после задания свойства. Изменение **CursorLocation** свойство не оказывает влияния на существующие соединения.  
  
 Возвращенные курсоры [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) метод наследуют значение этого параметра. **Набор записей** объекты будут автоматически наследовать этот параметр их связанные соединения.  
  
 Это свойство является чтение и запись на [подключения](../../../ado/reference/ado-api/connection-object-ado.md) или закрытый [записей](../../../ado/reference/ado-api/recordset-object-ado.md)и только для чтения на открытый **записей**.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** или **подключения** объекта, **CursorLocation** свойству можно присвоить только значение **adUseClient**.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
