---
title: SQLSetEnvAttr | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1b90e50881b39b1e943aad7d1cd6c23c90ff1d83
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35695455"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [Справочник по программированию ODBC](http://go.microsoft.com/fwlink/?LinkId=45250) определяет способ, с помощью которого драйверы ODBC должны интерпретировать спецификации атрибута **SQLSetEnvAttr** в приложениях, разработанных с использованием API ODBC 2.*x* или ODBC 3.*x* . Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соответствует следующим правилам.  
  
 Один из атрибутов, управляемых функцией **SQLSetEnvAttr** , указывает, нужно ли использовать пул соединений. Если пул соединений используется с ODBC-драйвером собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то параметр *DriverCompletion* должен быть установлен в значение SQL_DRIVER_NOPROMPT при подключении к [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) или **SQLConnect**.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLSetEnvAttr](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
