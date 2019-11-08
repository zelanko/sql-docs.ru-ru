---
title: Использование автоматической выборки с курсорами ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 98ac32d37598c3234a6a02320139e537b694ca07
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73784252"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Использование автоматической выборки с помощью курсоров ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]драйвер ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для собственного клиента поддерживает параметр автоматической выборки при использовании любого типа серверного курсора. При автоматической выборке функция **SQLExecute** или **SQLExecDirect** , открывающая курсор, также имеет неявную функцию [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST). Строки, составляющие первый набор строк, возвращаются в привязанные переменные приложения в ходе выполнения инструкции; это позволяет сэкономить одно обращение через сеть к серверу [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) не поддерживается, если включен параметр автоматической выборки. столбцы результирующего набора должны быть привязаны к переменным программы.  
  
 Приложения запрашивают автоматическую выборку, задавая для зависящего от драйвера атрибута инструкции SQL_SOPT_SS_CURSOR_OPTIONS значение SQL_CO_AF.  
  
## <a name="see-also"></a>См. также раздел  
 [Сведения о &#40;программировании курсора ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
