---
title: SQLGetCursorName | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a9d81199840f59ec7ac4b9c94b0d58c86b9eab52
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302162"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Если приложение не указывает имени курсора, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует его для приложения после создании курсора. Приложение может использовать **SQLGetCursorName** , чтобы получить определенное драйвером имя курсора для позиционированных инструкций UPDATE и DELETE. Приложению не требуется вызывать **SQLSetCursorName** , чтобы использовать преимущества позиционированных инструкций по обработке данных.  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLGetCursorName](https://go.microsoft.com/fwlink/?LinkId=59349)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
