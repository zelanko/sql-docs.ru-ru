---
description: Свойство Prompt (динамическое) (ADO)
title: Свойство Prompt — Dynamic (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
author: rothja
ms.author: jroth
ms.openlocfilehash: 67e8df1a59edecaf601f0ec4c5fd4b7782877e8d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990015"
---
# <a name="prompt-property-dynamic-ado"></a>Свойство Prompt (динамическое) (ADO)
Указывает, должен ли поставщик OLE DB запрашивать сведения об инициализации у пользователя.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает значение [коннектпромптенум](./connectpromptenum.md) .  
  
## <a name="remarks"></a>Remarks  
 **Prompt** — это динамическое свойство, которое может быть добавлено к коллекции [свойств](./properties-collection-ado.md) объекта [Connection](./connection-object-ado.md) поставщиком OLE DB. Для запроса сведений об инициализации поставщик OLE DB обычно отображает диалоговое окно для пользователя.  
  
 При закрытии **соединения** динамические свойства объекта [соединения](./connection-object-ado.md) теряются. Необходимо сбросить свойство **Prompt** , прежде чем повторно открыть **соединение** , чтобы использовать значение, отличное от значения по умолчанию.  
  
> [!NOTE]
>  Не указывайте, что поставщик должен запрашивать пользователя в сценариях, в которых пользователь не сможет ответить на это диалоговое окно. Например, пользователь не сможет ответить, если приложение выполняется в серверной системе, а не на клиенте пользователя, или если приложение выполняется в системе без входа пользователя в систему. В таких случаях приложение будет ожидать ответа в течение неограниченного времени и кажется заблокированным.  
  
## <a name="usage"></a>Использование  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>Применение  
 [Объект Connection (ADO)](./connection-object-ado.md)