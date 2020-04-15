---
title: Тип ODBC S'L для параметров, оцениваемых таблицей(ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6aae522544f4d9532dbc2d71db1b3d55ebee3da5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297845"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>Тип ODBC SQL для параметров, возвращающих табличное значение
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поддержка возвращающих табличное значение параметров обеспечивается новым типом ODBC SQL — SQL_SS_TABLE.  
  
## <a name="remarks"></a>Remarks  
 Тип SQL_SS_TABLE нельзя преобразовать в любой другой тип данных ODBC или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Если SQL_SS_TABLE используется в качестве типа данных C в параметре *ValueType* s'LBindParameter, или предпринимается попытка установить SQL_DESC_TYPE в дескрипторе параметра приложения (APD) для SQL_SS_TABLE, SQL_ERROR возвращается, и диагностическая запись генерируется с помощью s'LSTATE-HY003, "Недействительный тип буфера приложения".  
  
 Если SQL_DESC_TYPE устанавливается в IPD-записи в значение SQL_SS_TABLE, а соответствующая запись дескриптора параметра приложения не SQL_C_DEFAULT, то возвращается значение SQL_ERROR и создается диагностическая запись с кодом SQLSTATE=HY003 и сообщением «Недопустимый тип буфера приложения». Это может произойти с *ParameterType* s'LSetDescfield, S'LSetDescrec или S'LBindParameter.  
  
 Если параметр *TargetType* SQL_SS_TABLE при вызове S'LGetData, SQL_ERROR возвращается, и диагностическая запись генерируется с помощью s'LSTATE-HY003, "Недействительный тип буфера приложения".  
  
 Столбец возвращающего табличное значение параметра не может привязываться в виде типа SQL_SS_TABLE. Если функция **SQLBindParameter** вызывается с параметром *ParameterType* типа SQL_SS_TABLE, то возвращается значение SQL_ERROR и создается диагностическая запись с кодом SQLSTATE=HY004 и сообщением «Недопустимый тип данных SQL». Это также может произойти с S'LSetDescfield и S'LSetDesccRec.  
  
 Значения столбца возвращающего табличные значения параметра имеют те же возможности преобразования данных, как параметры и результирующие столбцы.  
  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях возвращающий табличное значение параметр может быть только входным параметром. Если предпринимается попытка установить SQL_DESC_PARAMETER_TYPE на значение, не SQL_PARAM_INPUT, через S'LBindParameter или S'LSetDesccField, SQL_ERROR возвращается, и диагностическая запись добавляется в выписку с S'LSTATE-HY105 и сообщение "Недействительный тип параметра".  
  
 Столбцы возвращающего табличное значение параметра не могут использовать в качестве параметра *StrLen_or_IndPtr*значение SQL_DEFAULT_PARAM, так как значения по умолчанию не поддерживаются возвращающими табличное значение параметрами. Вместо этого приложение может установить атрибут столбца SQL_CA_SS_COL_HAS_DEFAULT_VALUE в значение 1. Это значит, что во всех строках столбца будут значения по умолчанию. Если *StrLen_or_IndPtr* настроена на SQL_DEFAULT_PARAM, s'LExecute или S'LExecDirect вернется SQL_ERROR, и диагностическая запись будет добавлена в выписку с S'LSTATE-HY090 и сообщение "Недействий строки или длины буфера".  
  
## <a name="see-also"></a>См. также:  
 [Параметры, оцененные таблицей, &#40;&#41;ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
