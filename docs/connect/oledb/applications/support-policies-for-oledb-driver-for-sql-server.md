---
title: Политики поддержки для драйвера OLE DB для SQL Server | Документы Майкрософт
description: Политики поддержки для драйвера OLE DB для SQL Server
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 782745fa9957cd611aa875bec2f9b740b489f210
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53202013"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Политики поддержки для драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В этой статье описывается, как различные компоненты доступа к данным, которая может использоваться с драйвером OLE DB для SQL Server.  

## <a name="server-support"></a>Поддержка сервера  
 Драйвер OLE DB для SQL Server поддерживает подключения к [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)], [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)], [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)], и [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Поддерживаемые версии операционных систем  
 В следующей таблице перечислены операционных систем, поддерживающих драйвера OLE DB для SQL Server.  

|Поддерживаемые операционные системы|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012<br /><br />Microsoft Windows Server2012 R2<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>Политика поддержки ADO  
 Приложение ADO может пользоваться поставщиком OLE DB SQLOLEDB, который входит в состав Windows, если ему не требуются функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии.  

 Приложения ADO могут использовать драйвер OLE DB для SQL Server, но при этом они должны указать `DataTypeCompatibility=80` в строках подключения. Только функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] будут доступны, если в строке соединения указано значение `DataTypeCompatibility=80`.  

## <a name="ole-db-support-policies"></a>Политики поддержки OLE DB  
Приложения могут использовать поставщик OLE DB (SQLOLEDB), включенный в операционную систему Windows. Тем не менее, который находится в режиме обслуживания и больше не обновляется. Вам следует использовать драйвер OLE DB для SQL Server (MSOLEDBSQL).

## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
