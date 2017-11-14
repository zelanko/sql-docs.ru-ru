---
title: "Запрашивать динамические свойства (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 065656ea3023b1526573a48cd6d7d21eee6f6179
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="prompt-property-dynamic-ado"></a>Запрашивать динамические свойства (ADO)
Указывает, должен ли поставщик OLE DB запрашивать у пользователя сведения об инициализации.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md) значение.  
  
## <a name="remarks"></a>Замечания  
 **Запрос** является динамическим, который может быть добавлен к [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции с помощью поставщика OLE DB. Запрашивает сведения об инициализации, поставщики OLE DB обычно отображает диалоговое окно для пользователя.  
  
 Динамические свойства класса [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта были утеряны при **подключения** закрыт. **Prompt** свойства должен быть сброшен перед повторного открытия **подключения** использовать значение, отличное от по умолчанию.  
  
> [!NOTE]
>  Не следует указывать, что поставщик должен запросить пользователя в сценариях, в которых пользователь не будет отвечать на диалоговое окно. Например пользователь не сможет ответить, если приложение выполняется на сервере системы, а не на клиенте пользователя или если приложение выполняется в системе без вошедшего пользователя. В таких случаях приложение будет бесконечно ожидать ответа и зависать.  
  
## <a name="usage"></a>Использование  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>Объект применения  
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)

