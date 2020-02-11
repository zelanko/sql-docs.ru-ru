---
title: Атрибуты, влияющие на возвращающие табличное значение параметры
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor header field
- table-valued parameters (ODBC), statement attribute
ms.assetid: 089213b0-d368-4332-b2e5-b2bd8770c64f
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 56c8edb4aca4cad37c74e074bf9a1bd1dd8d36ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75246384"
---
# <a name="statement-attributes-that-affect-table-valued-parameters"></a>Атрибуты инструкции, влияющие на возвращающие табличное значение параметры
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В следующей таблице описаны атрибуты в поле дескриптора.  
  
|Имя атрибута|Тип|Description|  
|--------------------|----------|-----------------|  
|SQL_SOPT_SS_PARAM_FOCUS|SQLUINTEGER|Дополнительные сведения о SQL_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).|  
|SQL_SOPT_SS_NAME_SCOPE|SQLUINTEGER|Дополнительные сведения о SQL_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).|  
||||

## <a name="see-also"></a>См. также:  
 [Возвращающие табличное значение параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
