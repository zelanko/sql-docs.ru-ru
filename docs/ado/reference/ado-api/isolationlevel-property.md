---
title: "Свойство IsolationLevel | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Connection15::IsolationLevel
helpviewer_keywords: IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f9b94c3d33c04f71adbbf82c9a4aa672d04fc482
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>См. также:  
 [IsolationLevel и пример свойства режима (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel и пример свойства режима (VC ++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
