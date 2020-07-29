---
title: Компоненты драйвера OLE DB для SQL Server | Документация Майкрософт
description: Компоненты драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c88ef12d636dd5b10e1b7b3cd9418df3e058325b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007057"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Компоненты драйвера OLE DB для SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Компоненты Microsoft OLE DB Driver for SQL Server.  

|Компонент|Описание|  
|---------------|-----------------|  
|msoledbsql.dll|Файл библиотеки динамической компоновки (DLL), содержащий все функциональные возможности Microsoft OLE DB Driver for SQL Server.|  
|msoledbsqlr.rll|Сопутствующий файл ресурса для библиотеки Microsoft OLE DB Driver for SQL Server.|   
|msoledbsql.h|Файл заголовков для Microsoft OLE DB Driver for SQL Server, который содержит все новые определения, необходимые для использования Microsoft OLE DB Driver for SQL Server. Этот файл заголовка заменяет собой файл sqloledb.h.<br /><br /> Примечание. Вы можете использовать в одной программе ссылки на msoledbsql.h и sqloledb.h, но sqloledb.h в этом случае нужно определить первым.|  
|msoledbsql.lib|Файл библиотеки, необходимой для прямого вызова функции [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md), которая включена в Microsoft OLE DB Driver for SQL Server.<br /><br /> Примечание. Если в программном коде есть ссылка на файл msoledbsql.lib, необходимо убедиться, что файл msoledbsql.dll находится в системном пути разработчика и в системных путях пользователей, использующих данное приложение.|  

## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
