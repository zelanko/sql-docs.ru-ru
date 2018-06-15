---
title: SQLCancel | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cd188d69ba67c51c4b508d050ec91204b2f500bc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32948059"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) раздел о том, что в ODBC 2.x, если приложение вызывает **SQLCancel** Если обработка не выполняется в операторе **SQLCancel** действует так же, как  **SQLFreeStmt** с **SQL_CLOSE** параметр; это поведение определяется только для полноты и приложения должны вызывать метод **SQLFreeStmt** или  **SQLCloseCursor** закрытия курсора. Но даже если ваш [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственное клиентское приложение задает версию ODBC API 3.5.x или более поздней версии, **SQLCancel** функция будет использовать поведение ODBC 2.x.  
  
## <a name="see-also"></a>См. также  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
