---
title: "С помощью автоматической выборки с курсорами ODBC | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: af3960c80d52189cf45e4c836cf25714fd8b868b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="using-autofetch-with-odbc-cursors"></a>Использование автоматической выборки с помощью курсоров ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  При подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживает автоматическую выборку при использовании любого типа серверного курсора. Автоматической выборки **SQLExecute** или **SQLExecDirect** функцию, которая открывает курсор имеет неявный [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)функции (SQL_FIRST). Строки, составляющие первый набор строк, возвращаются в привязанные переменные приложения в ходе выполнения инструкции; это позволяет сэкономить одно обращение через сеть к серверу [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) не поддерживается, если включен параметр автоматической выборки; столбцы результирующего набора должны быть привязаны к переменным программы.  
  
 Приложения запрашивают автоматическую выборку, задавая для зависящего от драйвера атрибута инструкции SQL_SOPT_SS_CURSOR_OPTIONS значение SQL_CO_AF.  
  
## <a name="see-also"></a>См. также:  
 [Подробные сведения о программировании курсоров &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
