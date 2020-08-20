---
description: Создание профилей производительности драйвера (ODBC)
title: Создание профилей производительности драйвера ODBC
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f7245e4bdaf3196f9bb5e85ec6815b33f919e543
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486854"
---
# <a name="profiling-odbc-driver-performance-odbc"></a>Создание профилей производительности драйвера (ODBC)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Драйвер ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет два параметра для измерения производительности драйвера.  
  
 Драйвер ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может записывать статистические показатели производительности в файл. Журнал статистики — это файл с разделителями-знаками табуляции, который можно проанализировать в приложении электронных таблиц, поддерживающем файлы с разделителями-знаками табуляции, например в Microsoft Excel.  
  
 Драйвер также может регистрировать долго выполняемые запросы (запросы, на которые сервер не возвращает ответа в течение заданного времени). Эти запросы могут позднее анализироваться программистами и администраторами баз данных.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Данные производительности драйвера профиля &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data.md)  
  
-   [Регистрация долго выполняющихся запросов &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a>См. также:  
 [ODBC How-to Topics](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
  
