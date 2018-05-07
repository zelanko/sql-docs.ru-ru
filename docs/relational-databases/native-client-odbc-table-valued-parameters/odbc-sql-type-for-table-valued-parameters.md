---
title: Тип ODBC SQL для возвращающих табличные значения параметров | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cbf2b434d29033961608494478bc775946226ced
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>Тип ODBC SQL для параметров, возвращающих табличное значение
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Поддержка возвращающих табличное значение параметров обеспечивается новым типом ODBC SQL — SQL_SS_TABLE.  
  
## <a name="remarks"></a>Замечания  
 Тип SQL_SS_TABLE нельзя преобразовать в любой другой тип данных ODBC или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если тип SQL_SS_TABLE используется как тип данных C в *ValueType* устанавливаются параметр SQLBindParameter или попытка установить SQL_DESC_TYPE в записи дескриптора (APD) параметр приложения SQL_SS_TABLE, возвращается значение SQL_ERROR и создается запись диагностики с кодом SQLSTATE = hy003 и сообщением «недопустимый тип буфера приложения».  
  
 Если SQL_DESC_TYPE устанавливается в IPD-записи в значение SQL_SS_TABLE, а соответствующая запись дескриптора параметра приложения не SQL_C_DEFAULT, то возвращается значение SQL_ERROR и создается диагностическая запись с кодом SQLSTATE=HY003 и сообщением «Недопустимый тип буфера приложения». Это может произойти с *ParameterType* SQLSetDescField, SQLSetDescRec или SQLBindParameter.  
  
 Если *TargetType* параметр имеет тип SQL_SS_TABLE, при вызове метода SQLGetData, возвращается значение SQL_ERROR и создана диагностическая запись с кодом SQLSTATE = hy003 и сообщением «недопустимый тип буфера приложения».  
  
 Столбец возвращающего табличное значение параметра не может привязываться в виде типа SQL_SS_TABLE. Если функция **SQLBindParameter** вызывается с параметром *ParameterType* типа SQL_SS_TABLE, то возвращается значение SQL_ERROR и создается диагностическая запись с кодом SQLSTATE=HY004 и сообщением «Недопустимый тип данных SQL». Это также может произойти с SQLSetDescField и SQLSetDescRec.  
  
 Значения столбца возвращающего табличные значения параметра имеют те же возможности преобразования данных, как параметры и результирующие столбцы.  
  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях возвращающий табличное значение параметр может быть только входным параметром. Если попытка установить SQL_DESC_PARAMETER_TYPE значение, отличное от SQL_PARAM_INPUT SQLBindParameter или SQLSetDescField, возвращается значение SQL_ERROR и создается диагностическая запись добавляется в инструкцию с кодом SQLSTATE = HY105 и сообщением «недопустимый параметр тип».  
  
 Столбцы возвращающего табличное значение параметра не могут использовать в качестве параметра *StrLen_or_IndPtr*значение SQL_DEFAULT_PARAM, так как значения по умолчанию не поддерживаются возвращающими табличное значение параметрами. Вместо этого приложение может установить атрибут столбца SQL_CA_SS_COL_HAS_DEFAULT_VALUE в значение 1. Это значит, что во всех строках столбца будут значения по умолчанию. Если *StrLen_or_IndPtr* имеет значение SQL_DEFAULT_PARAM, для SQLExecute или SQLExecDirect вернет значение SQL_ERROR и создается диагностическая запись будет добавляться к инструкции с кодом SQLSTATE = HY090 и сообщением «Недопустимая длина строки или буфера».  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
