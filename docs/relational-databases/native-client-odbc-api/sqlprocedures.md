---
title: SQLProcedures | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a2b8d05b17507c5e8c940e1fa324decd5c0c5db1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68131233"
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Все хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращают какое-либо значение. **SQLProcedures** сообщает значение SQL_PT_FUNCTION столбцу результирующего набора PROCEDURE_TYPE.  
  
 **SQLProcedures** возвращает SQL_SUCCESS независимо от наличия значения существуют для *CatalogName, SchemaName* или *ProcName* параметров. Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 **SQLProcedures** может быть выполнена для статического серверного курсора. При попытке выполнить **SQLProcedures** для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, что тип курсора был изменен.  
  
 **SQLProcedures** возвращает сведения обо всех процедурах, имена которых соответствуют *ProcName* и могут быть выполнены текущим пользователем, или для которого текущий пользователь имеет разрешение VIEW DEFINITION.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLProcedures](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
