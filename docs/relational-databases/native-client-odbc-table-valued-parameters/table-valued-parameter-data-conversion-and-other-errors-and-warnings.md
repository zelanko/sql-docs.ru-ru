---
title: Конверсия параметров, оцененных таблицей,
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b5e130fcc4a1ccc3303117ca34abdc6510e815e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297820"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>Ошибки и предупреждения преобразования данных возвращающих табличное значение параметров и другие
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Значения столбцов возвращающих табличные значения параметров могут преобразовываться из клиентских типов данных в серверные и обратно таким же образом, как и значения других столбцов и параметров. Но поскольку возвращающий табличное значение параметр может содержать несколько столбцов и несколько строк, важно иметь возможность идентификации фактического значения там, где возникла ошибка.  
  
 При обнаружении ошибки или предупреждения в столбце параметра, возвращающего табличное значение, собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует диагностическую запись. Сообщение об ошибке содержит номер возвращающего табличное значение параметра, а также порядковый номер столбца и номер строки. Приложение может также использовать диагностические поля SQL_DIAG_SS_TABLE_COLUMN_NUMBER и SQL_DIAG_SS_TABLE_ROW_NUMBER внутри диагностических записей для определения того, какие значения ассоциируются с ошибками и предупреждениями. Эти диагностические поля доступны в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях.  
  
 Во всех прочих отношениях SQLSTATE и компоненты сообщений диагностических записей соответствуют существующим нормам функционирования ODBC. То есть, за исключением информации об идентификации параметра, строки и столбца, сообщения об ошибках имеют те же значения для параметров, оцениваемых таблицей, что и для параметров, не ценных таблицей.  
  
## <a name="see-also"></a>См. также:  
 [Параметры, оцененные таблицей, &#40;&#41;ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
