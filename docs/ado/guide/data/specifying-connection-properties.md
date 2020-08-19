---
description: Указание свойств подключения
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e1f7a26e66eae550bc740f2f9be5a3606650dcb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452836"
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
