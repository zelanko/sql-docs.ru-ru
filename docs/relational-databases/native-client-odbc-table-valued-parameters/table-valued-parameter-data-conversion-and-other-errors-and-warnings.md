---
title: "Табличное значение параметра данных преобразования, а также другие ошибки и предупреждения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef6e42cf00bc8b9b697590d5ebad971fd16a6b97
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>Ошибки и предупреждения преобразования данных возвращающих табличное значение параметров и другие
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Значения столбцов возвращающих табличные значения параметров могут преобразовываться из клиентских типов данных в серверные и обратно таким же образом, как и значения других столбцов и параметров. Но поскольку возвращающий табличное значение параметр может содержать несколько столбцов и несколько строк, важно иметь возможность идентификации фактического значения там, где возникла ошибка.  
  
 При обнаружении ошибки или предупреждения в столбце параметра, возвращающего табличное значение, собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует диагностическую запись. Сообщение об ошибке содержит номер возвращающего табличное значение параметра, а также порядковый номер столбца и номер строки. Приложение может также использовать диагностические поля SQL_DIAG_SS_TABLE_COLUMN_NUMBER и SQL_DIAG_SS_TABLE_ROW_NUMBER внутри диагностических записей для определения того, какие значения ассоциируются с ошибками и предупреждениями. Эти диагностические поля доступны в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях.  
  
 Во всех прочих отношениях SQLSTATE и компоненты сообщений диагностических записей соответствуют существующим нормам функционирования ODBC. Иными словами, если не считать сведения, идентифицирующие параметр, строку и столбец, сообщения об ошибках имеют те же значения для возвращающих табличные значения параметров, что и для параметров, не возвращающих табличные значения.  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличные значения параметры &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
