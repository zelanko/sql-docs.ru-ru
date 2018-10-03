---
title: Тип ODBC SQL для возвращающих табличные значения параметров | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90857b24fb467df0292beeb88fb9751e68204d12
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103934"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>Тип ODBC SQL для параметров, возвращающих табличное значение
  Поддержка возвращающих табличное значение параметров обеспечивается новым типом ODBC SQL — SQL_SS_TABLE.  
  
## <a name="remarks"></a>Примечания  
 Тип SQL_SS_TABLE нельзя преобразовать в любой другой тип данных ODBC или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если тип SQL_SS_TABLE используется как тип данных C в *ValueType* параметр SQLBindParameter или попытка присвоить свойству SQL_DESC_TYPE в записи дескриптора (APD) приложения параметр типа sql_ss_table, возвращается значение SQL_ERROR и создается запись диагностики с кодом SQLSTATE = hy003 и сообщением «недопустимый тип буфера приложения».  
  
 Если SQL_DESC_TYPE устанавливается в IPD-записи в значение SQL_SS_TABLE, а соответствующая запись дескриптора параметра приложения не SQL_C_DEFAULT, то возвращается значение SQL_ERROR и создается диагностическая запись с кодом SQLSTATE=HY003 и сообщением «Недопустимый тип буфера приложения». Это может произойти с *ParameterType* SQLSetDescField и SQLSetDescRec SQLBindParameter.  
  
 Если *TargetType* параметр имеет тип SQL_SS_TABLE, при вызове метода SQLGetData, возвращается значение SQL_ERROR и создается запись диагностики с кодом SQLSTATE = hy003 и сообщением «недопустимый тип буфера приложения».  
  
 Столбец возвращающего табличное значение параметра не может привязываться в виде типа SQL_SS_TABLE. Если `SQLBindParameter` вызывается с *ParameterType* типа SQL_SS_TABLE, возвращается значение SQL_ERROR и создается запись диагностики с кодом SQLSTATE = hy004 и сообщением «Недопустимый тип данных SQL». Это также может произойти с SQLSetDescField и SQLSetDescRec.  
  
 Значения столбца возвращающего табличные значения параметра имеют те же возможности преобразования данных, как параметры и результирующие столбцы.  
  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях возвращающий табличное значение параметр может быть только входным параметром. Если попытка установить SQL_DESC_PARAMETER_TYPE значение, отличное от SQL_PARAM_INPUT SQLBindParameter или SQLSetDescField, возвращается значение SQL_ERROR и создается диагностическая запись добавляется в инструкцию с кодом SQLSTATE = HY105 и сообщением «недопустимый параметр тип».  
  
 Столбцы возвращающего табличное значение параметра не могут использовать в качестве параметра *StrLen_or_IndPtr*значение SQL_DEFAULT_PARAM, так как значения по умолчанию не поддерживаются возвращающими табличное значение параметрами. Вместо этого приложение может установить атрибут столбца SQL_CA_SS_COL_HAS_DEFAULT_VALUE в значение 1. Это значит, что во всех строках столбца будут значения по умолчанию. Если *StrLen_or_IndPtr* устанавливается в значение SQL_DEFAULT_PARAM, SQLExecute или SQLExecDirect вернет значение SQL_ERROR и создается диагностическая запись добавляется в инструкцию с кодом SQLSTATE = HY090 и сообщением «Недопустимая длина строки или буфера».  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
