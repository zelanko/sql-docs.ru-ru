---
title: Указание свойств соединения | Документы Microsoft
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
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a91a6c1346f352c2ee55cef79d502d81ad8119ec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
