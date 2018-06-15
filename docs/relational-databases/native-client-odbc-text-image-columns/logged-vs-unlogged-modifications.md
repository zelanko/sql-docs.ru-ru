---
title: Журнал vs. Незафиксированных изменений | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-text-image-columns
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 010eebfd8c47ad288586f27a8f161164b2ac6b60
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32945209"
---
# <a name="logged-vs-unlogged-modifications"></a>Журнал vs. Незафиксированных изменений
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Приложение может запрашивать, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не журнала **текст**, **ntext**, и **изображения** изменения. Однако этот режим следует использовать очень осторожно. Он должен использоваться только для тех случаев, где **текст**, **ntext**, или **изображения** данные не являются критическими и владельцы данных готовы пожертвовать возможностью для восстановления данных на более высокая производительность.  
  
 Ведение журнала **текст**, **ntext**, и **изображения** изменений осуществляется путем вызова функции [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с  *Атрибут* равным SQL_SOPT_SS_ TEXTPTR_LOGGING и *ValuePtr* SQL_TL_ON или SQL_TL_OFF.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами text и image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
