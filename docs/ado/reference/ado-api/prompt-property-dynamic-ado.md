---
title: Запрашивать динамические свойства (ADO) | Документы Microsoft
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
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc7285d03db3edf52ddb89a91b2b73c5d3ae74c1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
