---
title: Требования к системе для драйвера OLE DB для SQL Server | Документы Майкрософт
description: Требования для драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- system requirements [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], system requirements
- OLE DB Driver for SQL Server, system requirements
- MSOLEDBSQL, system requirements
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a2ff38f4322209c7ed6eb46a5ba97f360ca3650b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821032"
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>Требования к системе для драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Чтобы использовать функции доступа к данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например режим MARS, необходимо установить следующее программное обеспечение:  

-   Драйвер OLE DB для SQL Server на клиентском компьютере.  

-   экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервере.   

> [!NOTE]  
>  Перед установкой данного программного обеспечения убедитесь, что вы вошли в систему с правами администратора.  

## <a name="operating-system-requirements"></a>Требования к операционной системе  
 Список операционных систем, поддерживающих драйвера OLE DB для SQL Server, см. в разделе [политики поддержки для драйвер OLE DB для SQL Server](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md).  

## <a name="sql-server-requirements"></a>Требования к SQL Server  
 Чтобы использовать драйвер OLE DB для SQL Server для доступа к данным в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных, необходимо иметь экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен.  

 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] поддерживает подключения с помощью всех версий компонентов MDAC, компонентов доступа к данным Windows и всех версий драйвера OLE DB для SQL Server. Когда клиент более старой версии соединяется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], неизвестные клиенту типы данных сервера сопоставляются типам, совместимым с версией клиента. Дополнительные сведения см. в подразделе «Совместимость типов данных для версий клиента» ниже в этом разделе.  

## <a name="cross-language-requirements"></a>Требования к версиям на разных языках  
 Английская версия драйвер OLE DB для SQL Server поддерживается на всех локализованных версиях поддерживаемых операционных систем. Локализованные версии драйвер OLE DB для SQL Server, поддерживаются в локализованных операционных системах, которые являются совпадает с языком локализованного драйвер OLE DB версии SQL Server. Локализованные версии драйвера OLE DB для SQL Server также поддерживаются английскими версиями операционных систем, если установлены соответствующие языковые настройки.  

 Для обновлений.  

-   Английской версии драйвер OLE DB для SQL Server можно обновить до любой локализованной версии драйвера OLE DB для SQL Server.  

-   Локализованные версии драйвер OLE DB для SQL Server можно обновить до локализованных версий драйвера OLE DB для SQL Server на том же языке.  

-   Локализованная версия драйвер OLE DB для SQL Server можно обновить до английской версии драйвера OLE DB для SQL Server.  

-   Локализованных версиях драйвер OLE DB для SQL Server не могут быть обновлены до локализованных драйвер OLE DB для SQL Server версии для другого локализованного языка.  

## <a name="data-type-compatibility-for-client-versions"></a>Совместимость типов данных для версий клиента  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и драйвер OLE DB для SQL Server сопоставляют новые типы данных со старыми, которые совместимы с клиентами низкого уровня, как показано в таблице ниже.  

 Приложения OLE DB и ADO могут использовать **DataTypeCompatibility** ключевое слово строки подключения с драйвер OLE DB для SQL Server для работы со старыми типами данных. При использовании **DataTypeCompatibility=80** клиенты OLE DB соединятся с помощью версии потока табличных данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], а не потока табличных данных. Это значит, что для [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних типов данных преобразование низкого уровня будет выполнено сервером, а не драйвером OLE DB для SQL Server. Это также означает, что функции, доступные при соединении, будут ограничиваться набором функций [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Попытки использовать новые типы данных или функций быстро определяются по вызовам API-интерфейса и ошибкам, возвращаемым вызывающему приложению, а не по попыткам передать недопустимые запросы на сервер.   


 IDBInfo::GetKeywords всегда будет возвращать список ключевых слов, который соответствует версии сервера для подключения и не зависит от **DataTypeCompatibility**.  

|Тип данных|собственный клиент SQL Server<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Драйвер OLE DB для SQL Server|Компоненты доступа к данным Windows, компоненты MDAC и<br /><br /> Драйвер OLE DB для приложений SQL Server OLE DB со свойством DataTypeCompatibility = 80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8 КБ)|определяемый пользователем тип|определяемый пользователем тип|определяемый пользователем тип|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|image|  
|varchar(max)|varchar|varchar|varchar|Текст|  
|nvarchar(max)|NVARCHAR|NVARCHAR|NVARCHAR|Ntext|  
|xml|xml|xml|xml|Ntext|  
|CLR UDT (> 8 КБ)|varbinary|определяемый пользователем тип|определяемый пользователем тип|image|  
|Дата|varchar|Дата|Дата|Varchar|  
|datetime2|varchar|datetime2|datetime2|Varchar|  
|datetimeoffset|varchar|datetimeoffset|datetimeoffset|Varchar|  
|time|varchar|time|time|Varchar|  

## <a name="see-also"></a>См. также:  
 [Драйвер OLE DB для SQL Server](../oledb/oledb-driver-for-sql-server.md)   
 [Установка драйвера OLE DB для SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
