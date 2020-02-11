---
title: SQLProcedures | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0001f1d6e45e855b884028a595a2b61263c2e58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046693"
---
# <a name="sqlprocedures"></a>SQLProcedures
  Все хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращают какое-либо значение. **SQLProcedures** reports SQL_PT_FUNCTION для PROCEDURE_TYPE столбца результирующего набора.  
  
 **SQLProcedures** возвращает SQL_SUCCESS, существуют ли значения для параметров *CatalogName, SchemaName* или *CNAME* . **SQLFetch** возвращает SQL_NO_DATA, если в этих параметрах используются недопустимые значения.  
  
 **SQLProcedures** может выполняться на статическом серверном курсоре. Попытка выполнить **SQLProcedures** для обновляемого (динамического или ключевого набора ключей) курсора возвратит SQL_SUCCESS_WITH_INFO, указывая, что тип курсора был изменен.  
  
 **SQLProcedures** возвращает сведения обо всех процедурах, имена которых совпадают с записями *CNAME* и могут быть выполнены текущим пользователем или для которого текущий пользователь предоставил разрешение View definition.  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLProcedures](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
