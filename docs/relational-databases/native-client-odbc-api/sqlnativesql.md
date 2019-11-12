---
title: SQLNativeSql | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e4d2baef508d6273ec6c89cca38961aa22742e69
ms.sourcegitcommit: b7618a2a7c14478e4785b83c4fb2509a3e23ee68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926017"
---
# <a name="sqlnativesql"></a>SQLNativeSql
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удовлетворяет запросы **SQLNativeSql** , не заходя на сервер. Эта функция выполняет эффективную проверку синтаксиса инструкций SQL. При проверке синтаксиса не устанавливается допустимость идентификаторов или результатов выражений в инструкциях SQL, а выполнение собственного SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , возвращенного функцией **SQLNativeSql** , может завершиться неудачей.  
  
## <a name="see-also"></a>См. также статью  
   [функции SQLNativeSql](https://go.microsoft.com/fwlink/?LinkID=59358)  
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
