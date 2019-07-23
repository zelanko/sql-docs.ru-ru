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
ms.openlocfilehash: 5a5124519bd95ec02e93a007d9881ec80814cfc8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989319"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Компоненты драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server содержит следующие компоненты:  

|Компонент|Описание|  
|---------------|-----------------|  
|мсоледбскл. dll|Файл библиотеки динамической компоновки (DLL), содержащий все драйверы OLE DB для функций SQL Server.|  
|мсоледбсклр. RLL|Сопутствующий файл ресурсов для драйвера OLE DB для SQL Server библиотеки.|   
|мсоледбскл. h|Драйвер OLE DB для SQL Server заголовочный файл, содержащий все новые определения, необходимые для использования драйвера OLE DB для SQL Server. Этот файл заголовка заменяет файл заголовка SQLOLEDB. h.<br /><br /> Примечание. Вы можете ссылаться на мсоледбскл. h и SQLOLEDB. h в той же программе, если в первую очередь определена SQLOLEDB. h.|  
|мсоледбскл. lib|Файл библиотеки, необходимый для непосредственного вызова функции [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) , которая является частью драйвера OLE DB для SQL Server.<br /><br /> Примечание. Если в программном коде есть ссылка на файл msoledbsql.lib, необходимо убедиться, что файл msoledbsql.dll находится в системном пути разработчика и в системных путях пользователей, использующих данное приложение.|  

## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
