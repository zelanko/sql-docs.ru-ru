---
title: "Указание свойств соединения | Документы Microsoft"
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
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80da1a4da2d2a04f6a73b05e57ab366d2cb40e97
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-connection-properties"></a>Указание свойств соединения
Можно указать объем информации, определяемое [строка подключения](../../../ado/guide/data/creating-a-connection-string.md) путем задания свойств **подключения** объекта до открытия соединения. Например, может получить тот же эффект, описанная в строке подключения [Создание строки подключения](../../../ado/guide/data/creating-a-connection-string.md) , используя следующий код.  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase имеет значение только после открытия подключения.  
  
> [!NOTE]
>  В ADO не должны использовать пароль, содержащий точку с запятой («;»), если пароль заключено в одинарные кавычки.
