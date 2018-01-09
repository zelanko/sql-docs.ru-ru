---
title: "SQLProcedures | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 23a0c1de61959b3a69766b6554f4c20694dea208
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Все хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращают какое-либо значение. **SQLProcedures** сообщает значение SQL_PT_FUNCTION результирующего набора procedure_type.  
  
 **SQLProcedures** возвращает SQL_SUCCESS независимо от наличия значения существуют для *CatalogName, SchemaName* или *ProcName* параметров. Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 **SQLProcedures** может быть выполнена для статического серверного курсора. Попытка выполнить **SQLProcedures** для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, указывающее на то, что тип курсора был изменен.  
  
 **SQLProcedures** возвращает сведения обо всех процедурах, имена которых соответствуют *ProcName* и могут быть выполнены текущим пользователем или для которого текущий пользователь имеет разрешение VIEW DEFINITION.  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLProcedures](http://go.microsoft.com/fwlink/?LinkId=59364)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
