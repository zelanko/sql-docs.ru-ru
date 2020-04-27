---
title: SQLColumnPrivileges | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 737ace72f201f3abe192393b1a1cc3747f5774e2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067760"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
  **SQLColumnPrivileges** возвращает значение, SQL_SUCCESS, существуют ли значения для параметров*CatalogName*, *SchemaName*, *TableName*или *ColumnName* . Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 **SQLColumnPrivileges** может выполняться на статическом серверном курсоре. Попытка выполнить **SQLColumnPrivileges** для обновляемого (динамического или ключевого набора ключей) курсора возвратит SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметре *CatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLColumnPrivileges](https://go.microsoft.com/fwlink/?LinkId=59335)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
