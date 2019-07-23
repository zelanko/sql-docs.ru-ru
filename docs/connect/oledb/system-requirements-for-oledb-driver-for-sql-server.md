---
title: Требования к системе для драйвера OLE DB для SQL Server | Документация Майкрософт
description: Требования для драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 02/12/2019
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
ms.openlocfilehash: cec8b2aca53f64e7a3883dbccddce1a330c8a6e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993777"
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>Требования к системе для драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Чтобы использовать функции доступа к данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например режим MARS, необходимо установить следующее программное обеспечение:  

-   Драйвер OLE DB для SQL Server на клиенте.  

-   экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервере.   

> [!NOTE]  
>  Перед установкой данного программного обеспечения убедитесь, что вы вошли в систему с правами администратора.  

## <a name="operating-system-requirements"></a>Требования к операционной системе  
 Список операционных систем, поддерживающих Драйвер OLE DB для SQL Server, см. в разделе [политики поддержки для драйвера OLE DB для SQL Server](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md).  

 ## <a name="azure-active-directory-authentication-requirements"></a>Требования для проверки подлинности Azure Active Directory  
 При использовании Azure Active Directory методов проверки подлинности с драйвером OLE DB убедитесь, что [Библиотека проверки подлинности Active Directory для SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) установлен. ADAL не требуется для других методов проверки подлинности или операций OLE DB.
Дополнительные сведения см. в статье об [использовании Azure Active Directory](features/using-azure-active-directory.md).

## <a name="sql-server-requirements"></a>требования SQL Server  
 Чтобы использовать драйвер OLE DB для SQL Server доступа к данным в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базах данных, необходимо [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установить экземпляр служб.  

 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] поддерживает подключения с помощью всех версий компонентов MDAC, компонентов доступа к данным Windows и всех версий драйвера OLE DB для SQL Server. Когда клиент более старой версии соединяется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], неизвестные клиенту типы данных сервера сопоставляются типам, совместимым с версией клиента. Дополнительные сведения см. в разделе [Совместимость типов данных для версий клиента](#data-type-compatibility-for-client-versions).  

## <a name="cross-language-requirements"></a>Требования к версиям на разных языках  
 Версия драйвера OLE DB для английского языка для SQL Server поддерживается во всех локализованных версиях поддерживаемых операционных систем. Локализованные версии драйвера OLE DB для SQL Server поддерживаются в локализованных операционных системах, имеющих тот же язык, что и локализованный драйвер OLE DB для SQL Server версии. Локализованные версии драйвера OLE DB для SQL Server также поддерживаются английскими версиями операционных систем, если установлены соответствующие языковые настройки.  

 Для обновлений.  

-   Версии драйвера OLE DB для английского языка для SQL Server можно обновить до локализованной версии драйвера OLE DB для SQL Server.  

-   Локализованные версии драйвера OLE DB для SQL Server можно обновить до локализованных версий OLE DB драйвера для SQL Server одного и того же языка.  

-   Локализованную версию драйвера OLE DB для SQL Server можно обновить до английской версии драйвера OLE DB для SQL Server.  

-   Локализованные версии драйвера OLE DB для SQL Server не могут быть обновлены до локализованного OLE DB драйвера для SQL Server версий другого локализованного языка.  

## <a name="data-type-compatibility-for-client-versions"></a>Совместимость типов данных для версий клиента  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и драйвер OLE DB для SQL Server сопоставляют новые типы данных со старыми, которые совместимы с клиентами низкого уровня, как показано в таблице ниже.  

 OLE DB и приложения ADO могут использовать ключевое слово строки подключения **DataTypeCompatibility диспетчера соединений** с драйвером OLE DB для SQL Server для работы с более старыми типами данных. При использовании **DataTypeCompatibility=80** клиенты OLE DB соединятся с помощью версии потока табличных данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], а не потока табличных данных. Это значит, что для [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних типов данных преобразование низкого уровня будет выполнено сервером, а не драйвером OLE DB для SQL Server. Это также означает, что функции, доступные при соединении, будут ограничиваться набором функций [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Попытки использовать новые типы данных или функций быстро определяются по вызовам API-интерфейса и ошибкам, возвращаемым вызывающему приложению, а не по попыткам передать недопустимые запросы на сервер.   


 Ключевое слово IDBInfo:: noreturn всегда возвращает список ключевых слов, соответствующий версии сервера в соединении, на который не влияет **DataTypeCompatibility диспетчера соединений**.  

|Тип данных|собственный клиент SQL Server<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Драйвер OLE DB для SQL Server|Компоненты доступа к данным Windows, компоненты MDAC и<br /><br /> Драйвер OLE DB для SQL Server OLE DB приложений с DataTypeCompatibility диспетчера соединений = 80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|Определяемый пользователем\<тип CLR (= 8 КБ)|определяемый пользователем тип|определяемый пользователем тип|определяемый пользователем тип|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|image|  
|varchar(max)|varchar|varchar|varchar|Текст|  
|nvarchar(max)|NVARCHAR|NVARCHAR|NVARCHAR|Ntext|  
|xml|xml|xml|xml|Ntext|  
|Определяемый пользователем тип CLR (> 8 КБ)|varbinary|определяемый пользователем тип|определяемый пользователем тип|image|  
|Дата|varchar|Дата|Дата|Varchar|  
|datetime2|varchar|datetime2|datetime2|Varchar|  
|datetimeoffset|varchar|datetimeoffset|datetimeoffset|Varchar|  
|time|varchar|time|time|Varchar|  

## <a name="see-also"></a>См. также раздел  
 [Драйвер OLE DB для SQL Server](../oledb/oledb-driver-for-sql-server.md)   
 [Установка драйвера OLE DB для SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
