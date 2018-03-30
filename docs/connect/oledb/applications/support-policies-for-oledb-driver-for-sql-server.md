---
title: Политики поддержки для драйвера OLE DB для SQL Server | Документы Microsoft
description: Политики поддержки для драйвера OLE DB для SQL Server
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 250b0dce301190454a911f5409425f486286047b
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Политики поддержки для драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этой статье обсуждается, как различные компоненты доступа к данным может использоваться с драйвером OLE DB для SQL Server.  

## <a name="server-support"></a>Поддержка сервера  
 Драйвер OLE DB для SQL Server поддерживает подключения к [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)],[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)], [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)], и [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Поддерживаемые версии операционных систем  
 В следующей таблице перечислены операционных систем, поддерживающих драйвер OLE DB для SQL Server.  

|Поддерживаемые операционные системы|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012<br /><br />Microsoft Windows Server 2012 R2<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>Политика поддержки ADO  
 Приложение ADO может пользоваться поставщиком OLE DB SQLOLEDB, который входит в состав Windows, если ему не требуются функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии.  

 Приложения ADO могут использовать драйвер OLE DB для SQL Server, но при этом они необходимо указать `DataTypeCompatibility=80` в строках подключения. Только функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] будут доступны, если в строке соединения указано значение `DataTypeCompatibility=80`.  

## <a name="ole-db-support-policies"></a>Политики поддержки OLE DB  
Приложения могут использовать поставщик OLE DB (SQLOLEDB), входящий в состав операционной системы Windows. Тем не менее, который находится в режиме обслуживания и больше не обновляется. Вам следует использовать драйвер OLE DB для SQL Server (MSOLEDBSQL).

## <a name="see-also"></a>См. также  
 [Построение приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
