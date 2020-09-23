---
title: Требования к системе для драйвера OLE DB для SQL Server
description: Сведения о предварительных требованиях к программному обеспечению, необходимых для использования функций доступа к данным SQL Server, например функции MARS, в OLE DB Driver for SQL Server.
ms.custom: ''
ms.date: 03/18/2020
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c86f62f98e81ce3c4fdd86e1e79e8f73e1422851
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861810"
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>Требования к системе для драйвера OLE DB для SQL Server

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Чтобы использовать функции доступа к данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например режим MARS, необходимо установить следующее программное обеспечение:  

* OLE DB Driver for SQL Server на клиенте.  
* экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервере.

> [!NOTE]  
> Перед установкой данного программного обеспечения убедитесь, что вы вошли в систему с правами администратора.  

## <a name="operating-system-requirements"></a>Требования к операционной системе  

Список операционных систем, поддерживающих OLE DB Driver for SQL Server, см. в статье [Support policies for OLE DB Driver for SQL Server](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md) (Политики поддержки для драйвера OLE DB для SQL Server).  

## <a name="azure-active-directory-authentication-requirements"></a>Требования для проверки подлинности Azure Active Directory  

При использовании методов проверки подлинности Active Directory с драйвером OLE DB для SQL Server ***до*** версии 18.3 должна быть установлена [Библиотека проверки подлинности Active Directory для SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072). (Версия 18.3 включает зависимость как часть пакета установщика.) Для других методов проверки подлинности или операций OLE DB ADAL не требуется. Дополнительные сведения см. в разделе: [Использование Azure Active Directory](features/using-azure-active-directory.md)

## <a name="sql-server-requirements"></a>требования SQL Server  

Чтобы использовать Драйвер OLE DB for SQL Server для доступа к данным из баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо иметь установленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] поддерживает подключения с помощью всех версий компонентов MDAC, компонентов доступа к данным Windows и всех версий драйвера OLE DB для SQL Server. Когда клиент более старой версии соединяется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], неизвестные клиенту типы данных сервера сопоставляются типам, совместимым с версией клиента. Дополнительные сведения см. в разделе [Совместимость типов данных для версий клиента](#data-type-compatibility-for-client-versions).  

## <a name="cross-language-requirements"></a>Требования к версиям на разных языках  

Англоязычная версия OLE DB Driver for SQL Server поддерживается на всех локализованных версиях поддерживаемых операционных систем. Локализованные версии OLE DB Driver for SQL Server поддерживаются в локализованных операционных системах на том же языке, что и локализованная версия OLE DB Driver for SQL Server. Локализованные версии драйвера OLE DB для SQL Server также поддерживаются английскими версиями операционных систем, если установлены соответствующие языковые настройки.  

Для обновлений.  

* Англоязычные версии OLE DB Driver for SQL Server можно обновить до локализованной версии OLE DB Driver for SQL Server.  
* Локализованные версии OLE DB Driver for SQL Server можно обновить до локализованных версий OLE DB Driver for SQL Server одного и того же языка.  
* Локализированная версия OLE DB Driver for SQL Server можно обновить до англоязычной версии OLE DB Driver for SQL Server.  
* Локализованные версии OLE DB Driver for SQL Server не могут быть обновлены до локализованного OLE DB Driver for SQL Server версий другого локализованного языка.  

## <a name="data-type-compatibility-for-client-versions"></a>Совместимость типов данных для версий клиента  

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и драйвер OLE DB для SQL Server сопоставляют новые типы данных со старыми, которые совместимы с клиентами низкого уровня, как показано в таблице ниже.  

Для работы со старыми типами данных приложения OLE DB и ADO могут использовать ключевое слово **DataTypeCompatibility** строки подключения с OLE DB Driver for SQL Server. При использовании **DataTypeCompatibility=80** клиенты OLE DB соединятся с помощью версии потока табличных данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], а не потока табличных данных. Это значит, что для [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних типов данных преобразование низкого уровня будет выполнено сервером, а не драйвером OLE DB для SQL Server. Это также означает, что функции, доступные при соединении, будут ограничиваться набором функций [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Попытки использовать новые типы данных или функций быстро определяются по вызовам API-интерфейса и ошибкам, возвращаемым вызывающему приложению, а не по попыткам передать недопустимые запросы на сервер.  

IDBInfo::GetKeywords всегда будет возвращать список ключевых слов, соответствующий версии сервера при соединении и не затронутый **DataTypeCompatibility**.  

|Тип данных|собственный клиент SQL Server<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Драйвер OLE DB для SQL Server|Компоненты доступа к данным Windows, компоненты MDAC и<br /><br /> Приложения OLE DB Driver for SQL Server со свойством DataTypeCompatibility=80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|определяемый пользователем тип среды CLR (\<= 8 КБ)|определяемый пользователем тип|определяемый пользователем тип|определяемый пользователем тип|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|Образ —|  
|varchar(max)|varchar|varchar|varchar|текст|  
|nvarchar(max)|nvarchar|nvarchar|nvarchar|Ntext|  
|Xml|Xml|Xml|Xml|Ntext|  
|определяемый пользователем тип среды CLR (> 8 КБ)|varbinary|определяемый пользователем тип|определяемый пользователем тип|Образ —|  
|Дата|varchar|Дата|Дата|Varchar|  
|datetime2|varchar|datetime2|datetime2|Varchar|  
|datetimeoffset|varchar|datetimeoffset|datetimeoffset|Varchar|  
|time|varchar|time|time|Varchar|  

## <a name="see-also"></a>См. также раздел  

[Драйвер OLE DB для SQL Server](../oledb/oledb-driver-for-sql-server.md)  
[Установка драйвера OLE DB для SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
