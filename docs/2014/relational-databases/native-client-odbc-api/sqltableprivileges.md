---
title: SQLTablePrivileges | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTablePrivileges function
ms.assetid: 8cce22d5-28b1-4b50-a5bc-1de03e0ffd6b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51492e55fd3c34c099a5f53187d1b2a9875ce7e3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63188640"
---
# <a name="sqltableprivileges"></a>SQLTablePrivileges
  Функция**SQLTablePrivileges** может быть выполнена для статического курсора. При попытке выполнить метод **SQLTablePrivileges** для обновляемого курсора (динамического или управляемого набором ключей) будет возвращено значение SQL_SUCCESS_WITH_INFO, которое указывает на то, что тип курсора был изменен.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметре *CatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLTablePrivileges] (https://go.microsoft.com/fwlink/?LinkId=59373\)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
