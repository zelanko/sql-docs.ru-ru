---
title: СЗЛПроцедуры Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 14ff76504c9a36657be60ba4855cf252474071d7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302375"
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Все хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращают какое-либо значение. **Отчеты s'LProcedures** SQL_PT_FUNCTION для столбца набора результатов PROCEDURE_TYPE.  
  
 **SLProcedures** возвращается SQL_SUCCESS, существуют ли значения для параметров *CatalogName, SchemaName* или *ProcName.* Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 **Процедуры S'Lprocedures** могут быть выполнены на статическом курсоре сервера. Попытка выполнить **S'LProcedures** на курсоре updatable (динамическом или клавиатурном) вернет SQL_SUCCESS_WITH_INFO, что указывает на изменение типа курсора.  
  
 **SLProcedures** возвращает информацию о любых процедурах, имена которых совпадают с *ProcName* и могут быть выполнены текущим пользователем, или для которых текущему пользователю было предоставлено разрешение VIEW DEFINITION.  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LProcedures](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
