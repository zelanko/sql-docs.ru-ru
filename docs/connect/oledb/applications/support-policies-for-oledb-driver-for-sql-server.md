---
title: Политики поддержки для драйвера OLE DB для SQL Server | Документация Майкрософт
description: Политики поддержки для драйвера OLE DB для SQL Server
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 1ae0e332de1d1e673cfd4fff1e288acafa4a0619
ms.sourcegitcommit: b016c01c47bc08351d093a59448d895cc170f8c3
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118142"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Политики поддержки для драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В этой статье описывается, как можно использовать различные компоненты доступа к данным с драйвером OLE DB для SQL Server.  

## <a name="server-support"></a>Поддержка сервера  
 Драйвер OLE DB для SQL Server поддерживает соединения с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)],, [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)]и [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Поддерживаемые версии операционных систем  
 В следующей таблице перечислены операционные системы, поддерживающие драйвер OLE DB для SQL Server.  

| Поддерживаемые операционные системы |  |
|--------------------------------------|---------------------------------|   
| [Обновление](https://go.microsoft.com/fwlink/?linkid=2073785) + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061) для Microsoft Windows 8.1 + Апрель 2014<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012 + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows Server 2012 R2, [Апрель 2014, обновление](https://go.microsoft.com/fwlink/?linkid=2073785) + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows Server 2016<br /><br />Microsoft Windows Server 2019 |  |


## <a name="ado-support-policies"></a>Политики поддержки ADO  
 Приложения ADO могут использовать поставщик OLE DB SQLOLEDB, который содержится в Windows, если для них не требуются функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии.  

 Приложения ADO могут использовать драйвер OLE DB для SQL Server, но если это так, они должны указывать `DataTypeCompatibility=80` в строках подключения. Только функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] будут доступны, если в строке соединения указано значение `DataTypeCompatibility=80`.  

## <a name="ole-db-support-policies"></a>Политики поддержки OLE DB  
Приложения могут использовать поставщик OLE DB (SQLOLEDB), включенный в операционную систему Windows. Однако он находится в режиме обслуживания и больше не обновляется. Вместо этого используйте драйвер OLE DB для SQL Server (МСОЛЕДБСКЛ).

## <a name="see-also"></a>См. также раздел  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
