---
title: Политики поддержки для драйвера OLE DB для SQL Server | Документация Майкрософт
description: Политики поддержки для драйвера OLE DB для SQL Server
ms.date: 05/25/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7e4b77a700d494f1ed8f11a0004c60b37c5cc361
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007041"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Политики поддержки для драйвера OLE DB для SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

В этой статье рассматриваются способы использования разных компонентов доступа к данным в сочетании с OLE DB Driver for SQL Server.  

## <a name="sql-version-support"></a>Поддержка версий SQL  

Драйвер OLE DB Driver for SQL Server проверяется с помощью подключения к следующим версиям SQL Server и поддерживает эти подключения.

| Версия драйвера | База данных SQL Azure | Хранилище SQL | Управляемый экземпляр SQL Azure | SQL Server 2019 | SQL Server 2017 | SQL Server 2016 | SQL Server 2014 | SQL Server 2012 |
|----|-|-|-|-|-|-|-|-|
|18.4|Да|Да|Да|Да|Да|Да|Да|Да|
|18.3|Да|Да|Да|Да|Да|Да|Да|Да|
|18.2|Да|Да|Да|Да|Да|Да|Да|Да|
|18.1|Да|Да|Да| |Да|Да|Да|Да|
|18.0|Да|Да|Да| |Да|Да|Да|Да|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="supported-operating-system-versions"></a>Поддерживаемые версии операционных систем  

В следующей таблице приведен список операционных систем, которые поддерживаются OLE DB Driver for SQL Server.  

| Версия драйвера | Windows Server 2019 | Windows Server 2016 | Windows Server 2012<sup>1</sup> | Windows Server 2012 R2<sup>2</sup> | Windows 10 | Windows 8.1<sup>3</sup> |
|----|-|-|-|-|-|-|
|18.4|Да|Да|Да|Да|Да|Да|
|18.3|Да|Да|Да|Да|Да|Да|
|18.2|Да|Да|Да|Да|Да|Да|
|18.1| |Да|Да|Да|Да|Да|
|18.0| |Да|Да|Да|Да|Да|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

<sup>1</sup> Поддерживается в Windows Server 2012 с обновлением [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061).  
<sup>2</sup> Поддерживается в Windows Server 2012 R2 с [обновлением за апрель 2014 г.](https://go.microsoft.com/fwlink/?linkid=2073785) и обновлением [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061).  
<sup>3</sup> Поддерживается в Windows 8.1 с [обновлением за апрель 2014 г.](https://go.microsoft.com/fwlink/?linkid=2073785) и обновлением [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061).  

## <a name="ado-support-policies"></a>Политики поддержки ADO  

Приложения ADO могут использовать поставщик OLE DB SQLOLEDB, который содержится в Windows, если для них не требуются функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии.  

Приложения ADO могут также использовать OLE DB Driver for SQL Server, но для этого в них нужно указать `DataTypeCompatibility=80` в строке подключения. Только функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] будут доступны, если в строке соединения указано значение `DataTypeCompatibility=80`.  

## <a name="ole-db-support-policies"></a>Политики поддержки OLE DB  

Приложения могут использовать поставщик OLE DB (SQLOLEDB), включенный в операционную систему Windows. Однако он находится в режиме обслуживания и больше не обновляется. Лучше использовать OLE DB Driver for SQL Server (MSOLEDBSQL)

## <a name="see-also"></a>См. также раздел  

[Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)
