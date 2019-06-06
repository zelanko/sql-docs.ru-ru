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
manager: jroth
ms.openlocfilehash: 344956b349e51a448a768988ff5062bfbc532562
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698425"
---
# <a name="cursorlocation-property-ado"></a>Свойство CursorLocation (ADO)
Указывает расположение службы курсора.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Long** значение, которое может быть присвоено одно из [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) значения.  
  
## <a name="remarks"></a>Примечания  
 Это свойство позволяет выбирать различные библиотеки курсоров, доступ к поставщику. Как правило можно выбрать между использованием библиотеку курсор на стороне клиента или один, который находится на сервере.  
  
 Значение этого свойства влияет на подключение только в том случае, после задания свойства. Изменение **CursorLocation** свойство не влияет на существующие подключения.  
  
 Возвращенные курсоры [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) метод будут наследовать этот параметр. **Набор записей** объекты будут автоматически наследовать этот параметр из их связанные соединения.  
  
 Это свойство доступно для чтения/записи на [подключения](../../../ado/reference/ado-api/connection-object-ado.md) или закрытого [записей](../../../ado/reference/ado-api/recordset-object-ado.md)и только для чтения при открытии **записей**.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** или **подключения** объекта, **CursorLocation** свойство может устанавливаться только для **adUseClient**.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Приложение а. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
