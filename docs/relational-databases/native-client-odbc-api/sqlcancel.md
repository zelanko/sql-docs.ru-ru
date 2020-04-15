---
title: СЗЛКсонск (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2db2c4b66940a81dd65064ee730cd683e2206a58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302648"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Тема [S'LCancel](https://go.microsoft.com/fwlink/?LinkId=203516) говорит о том, что в ODBC 2.x, если приложение вызывает **S'LCancel,** когда в выписке не выполняется обработка, **S'LCancel** имеет тот же эффект, что и **s-LFreeStmt** с **SQL_CLOSE** опцией; такое поведение определяется только для полноты, и приложения должны вызывать **S'LFreeStmt** или **S'LCloseCursor,** чтобы закрыть курсоры. Но даже [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если ваше приложение Native Client устанавливает версию ODBC API на 3.5.x или позже, функция **S'LCancel** будет использовать поведение ODBC 2.x.  
  
## <a name="see-also"></a>См. также:  
 [СЗЛКсонс](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
