---
title: "Свойство IsolationLevel | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b66b246ef3bc64e841ec6322de41ba0fc1e7af97
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="isolationlevel-property"></a>Свойство IsolationLevel
Указывает уровень изоляции для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md) значение. Значение по умолчанию — **adXactReadCommitted**.  
  
## <a name="remarks"></a>Remarks  
 Используйте **IsolationLevel** свойство, чтобы задать уровень изоляции **подключения** объекта. Параметр вступает в силу только при следующем вызове [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) метод. Если уровень изоляции, запрашивается недоступен, поставщик может возвращать больше следующий уровень изоляции без обновления **IsolationLevel** свойство.  
  
 **IsolationLevel** свойство доступно для чтения/записи.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **подключения** объекта, **IsolationLevel** может быть задано только в **adXactUnspecified**. Так как пользователи работают с отключенной **записей** объектов на стороне клиента кэша, может быть многопользовательской проблемы. Для экземпляра попытку обновления той же записи двух различных пользователей удаленной службы данных просто позволяет пользователю, выполняющему сначала обновляет запись для «win». Запрос на обновление второго пользователя будут завершаться ошибкой.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [IsolationLevel и пример свойства режима (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel и пример свойства режима (VC ++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
