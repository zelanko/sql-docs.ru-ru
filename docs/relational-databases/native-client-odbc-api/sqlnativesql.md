---
title: SQLNativeSql | Документы Microsoft
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
apitype: DLLExport
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dd37fa846e25afc3e2a52adb9dbfbcb2bfbe3bc2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlnativesql"></a>SQLNativeSql
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удовлетворяет запросы **SQLNativeSql** , не заходя на сервер. Эта функция выполняет эффективную проверку синтаксиса инструкций SQL. При проверке синтаксиса не устанавливается допустимость идентификаторов или результатов выражений в инструкциях SQL, а выполнение собственного SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , возвращенного функцией **SQLNativeSql** , может завершиться неудачей.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLNativeSql](http://go.microsoft.com/fwlink/?LinkID=59358)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
