---
title: Задание свойств соединения | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5aee5946f3087956a0117b88f4044ef8a6c9bd9f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924131"
---
# <a name="specifying-connection-properties"></a>Указание свойств подключения
Можно указать большую часть сведений, указанных в [строке подключения](../../../ado/guide/data/creating-a-connection-string.md) , задав свойства объекта **соединения** перед открытием соединения. Например, можно добиться того же результата, что и в строке подключения, описанной в разделе [Создание строки подключения](../../../ado/guide/data/creating-a-connection-string.md) с помощью следующего кода.  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase задается только после открытия подключения.  
  
> [!NOTE]
>  В ADO не следует использовать пароль, содержащий точку с запятой (";"), если пароль не заключен в одинарные кавычки.
