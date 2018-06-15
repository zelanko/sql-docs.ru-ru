---
title: Требования к системе для драйвера OLE DB для SQL Server | Документы Microsoft
description: Требования для драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- system requirements [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], system requirements
- OLE DB Driver for SQL Server, system requirements
- MSOLEDBSQL, system requirements
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: e109f228d8b902e5c34b4ed5731b80e315fffe3c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32859339"
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>Требования к системе для драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Чтобы использовать функции доступа к данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например режим MARS, необходимо установить следующее программное обеспечение:  

-   Драйвер OLE DB для SQL Server на клиентском компьютере.  

-   экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервере.   

> [!NOTE]  
>  Перед установкой данного программного обеспечения убедитесь, что вы вошли в систему с правами администратора.  

## <a name="operating-system-requirements"></a>Требования к операционной системе  
 Список операционных систем, поддерживающих драйвер OLE DB для SQL Server см. в разделе [политики поддержки для драйвер OLE DB для SQL Server](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md).  

## <a name="sql-server-requirements"></a>Требования к SQL Server  
 Чтобы использовать драйвер OLE DB для SQL Server для доступа к данным в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных, необходимо иметь установленный экземпляр из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен.  

 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] поддерживает соединения со всеми версиями компонентов MDAC, компонентов доступа к данным Windows и все версии драйвера OLE DB для SQL Server. Когда клиент более старой версии соединяется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], неизвестные клиенту типы данных сервера сопоставляются типам, совместимым с версией клиента. Дополнительные сведения см. в подразделе «Совместимость типов данных для версий клиента» ниже в этом разделе.  

## <a name="cross-language-requirements"></a>Требования к версиям на разных языках  
 Английская версия драйвер OLE DB для SQL Server поддерживается на всех локализованных версиях поддерживаемых операционных систем. Локализованные версии драйвер OLE DB для SQL Server поддерживаются в локализованных операционных системах на том же языке, как локализованные драйвер OLE DB версии SQL Server. Локализованные версии драйвер OLE DB для SQL Server также поддерживаются в английских версиях поддерживаемых операционных систем, при условии, что установлены совпадающие языковые настройки.  

 Для обновлений.  

-   Драйвер OLE DB для SQL Server английской версии могут обновляться до любой локализованной версии драйвер OLE DB для SQL Server.  

-   Локализованные версии драйвер OLE DB для SQL Server можно обновить до локализованных версий драйвера OLE DB для SQL Server на том же языке.  

-   Локализованная версия драйвер OLE DB для SQL Server можно обновить до английской версии драйвера OLE DB для SQL Server.  

-   Локализованные версии драйвер OLE DB для SQL Server не удается обновить для локализованных драйвер OLE DB для SQL Server версии для другого локализованного языка.  

## <a name="data-type-compatibility-for-client-versions"></a>Совместимость типов данных для версий клиента  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и драйвер OLE DB для SQL Server карты новые типы данных со старыми, совместимой с клиентами низкого уровня, как показано в следующей таблице.  

 Приложения OLE DB и ADO могут использовать **DataTypeCompatibility** ключевое слово строки подключения с драйвер OLE DB для SQL Server для работы со старыми типами данных. Когда **DataTypeCompatibility = 80**, клиенты OLE DB соединятся с помощью [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] потока табличных данных (TDS) версии, а не потока табличных данных. Это означает, что для [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних типов данных преобразование низкого уровня будет выполняться на сервере, а не драйвер OLE DB для SQL Server. Это также означает, что функции, доступные при соединении, будут ограничиваться набором функций [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Попытки использовать новые типы данных или функций быстро определяются по вызовам API-интерфейса и ошибкам, возвращаемым вызывающему приложению, а не по попыткам передать недопустимые запросы на сервер.   


 IDBInfo::GetKeywords всегда будет возвращать список ключевых слов, который соответствует версии сервера для соединения и не зависит от **DataTypeCompatibility**.  

|Тип данных|собственный клиент SQL Server<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Драйвер OLE DB для SQL Server|Компоненты доступа к данным Windows, компоненты MDAC и<br /><br /> Драйвер OLE DB для приложений SQL Server OLE DB со свойством DataTypeCompatibility = 80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|Определяемый пользователем тип CLR (\<= 8 КБ)|определяемый пользователем тип|определяемый пользователем тип|определяемый пользователем тип|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|image|  
|varchar(max)|varchar|varchar|varchar|Текст|  
|nvarchar(max)|nvarchar|nvarchar|nvarchar|Ntext|  
|xml|xml|xml|xml|Ntext|  
|CLR UDT (> 8 КБ)|varbinary|определяемый пользователем тип|определяемый пользователем тип|image|  
|date|varchar|date|date|Varchar|  
|datetime2|varchar|datetime2|datetime2|Varchar|  
|datetimeoffset|varchar|datetimeoffset|datetimeoffset|Varchar|  
|time|varchar|time|time|Varchar|  

## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server](../oledb/oledb-driver-for-sql-server.md)   
 [Установка драйвера OLE DB для SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
