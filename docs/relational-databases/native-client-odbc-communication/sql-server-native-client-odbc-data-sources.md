---
title: СЗЛ Сервер Родной Клиент ODBC Источники данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 46f0a6bf7fae4ba94395bb228066684faad23b96
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305461"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>Источники данных ODBC собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Имя источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (data source name, DSN) указывает источник данных ODBC, содержащий всю информацию, нужную ODBC-приложению для соединения с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на конкретном сервере. Задать имя источника данных ODBC можно двумя способами.  
  
-   На клиентском компьютере, открыть административные инструменты в панели управления, и дважды нажмите **на источники данных (ODBC)**. Откроется окно администратора источника данных ODBC, с помощью которого создается DSN.  
  
-   В приложении ODBC позвоните по [телефону S'LConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md).  
  
 Источник данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующие данные.  
  
-   Имя источника данных.  
  
-   Всю информацию, нужную для подключения к конкретному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Базу данных, используемую по умолчанию в конкретном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (необязательный параметр).  
  
-   Настройки: например различные параметры ANSI, местонахождение журнала для занесения показателей производительности и т. п. (необязательные параметры).  
  
 Приложение ODBC не обязательно должно использовать для подключения источник данных. Однако в этом случае приложение обязано предоставить функции соединения ODBC ту же информацию о соединении, которую драйвер в противном случае нашел бы в DSN.  
  
## <a name="see-also"></a>См. также:  
 [Общение с сервером &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
