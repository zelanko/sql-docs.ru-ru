---
title: Многопоточные приложения | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9c64c45331ec5f8efe11ee75abb065201cda0714
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009786"
---
# <a name="creating-a-driver-application---multithreaded-applications"></a>Создание приложения драйвера. Многопоточные приложения
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] является многопоточным драйвером. Написание многопоточного приложения — альтернатива использованию асинхронных вызовов для обработки нескольких вызовов ODBC. Поток может выполнить асинхронный вызов ODBC, а другие потоки могут обрабатываться, пока первый поток ожидает ответа на свой вызов. Эта модель эффективнее по сравнению с асинхронными вызовами, поскольку исключает такие издержки, как сетевой трафик и повторные вызовы функций ODBC с целью проверки значения SQL_STILL_EXECUTING.  
  
 Асинхронный режим все же остается эффективным методом обработки. Выигрыш в производительности многопоточной модели недостаточен, чтобы стала оправданной переработка асинхронных приложений. Если пользователям приходится преобразовывать приложения DB-Library, в которых используется асинхронная модель DB-Library, то проще преобразовать их в асинхронную модель ODBC.  
  
## <a name="see-also"></a>См. также  
 [Создание драйвера ODBC для собственного клиента SQL Server](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
  
