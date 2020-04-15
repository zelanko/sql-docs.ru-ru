---
title: Системные требования к родному клиенту сервера S'L (ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- system requirements [SQL Server Native Client]
- data access [SQL Server Native Client], system requirements
- SQL Server Native Client, system requirements
- SQLNCLI, system requirements
ms.assetid: 1c8e2f8a-a440-44da-8e3a-af632d34c52c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bdf5d2de1c465300be803386e75acecfb61db93b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305053"
---
# <a name="system-requirements-for-sql-server-native-client"></a>Системные требования для собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Чтобы использовать функции доступа к данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например режим MARS, необходимо установить следующее программное обеспечение:  
  
-   собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на клиенте;  
  
-   экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервере.  
  
 Собственному клиенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется установщик Windows версии 3.0. Установщик Windows версии 3.0 уже установлен в ОС [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Для всех других платформ необходимо его установить явно. Для получения дополнительной информации [см.](https://www.microsoft.com/download/details.aspx?id=16821)  
  
> [!NOTE]  
>  Перед установкой данного программного обеспечения убедитесь, что вы вошли в систему с правами администратора.  
  
## <a name="operating-system-requirements"></a>Требования к операционной системе  
 Список операционных систем, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживающих native-клиента, можно узнать о [политике поддержки для клиента S'L Server.](../../relational-databases/native-client/applications/support-policies-for-sql-server-native-client.md)  
  
## <a name="sql-server-requirements"></a>Требования к SQL Server  
 Чтобы использовать собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для доступа к данным из баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо иметь установленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] поддерживает подключения с помощью всех версий компонентов MDAC, компонентов доступа к данным Windows и всех версий собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда клиент более старой версии соединяется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], неизвестные клиенту типы данных сервера сопоставляются типам, совместимым с версией клиента. Дополнительные сведения см. в подразделе «Совместимость типов данных для версий клиента» ниже в этом разделе.  
  
## <a name="cross-language-requirements"></a>Требования к версиям на разных языках  
 Английская версия собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживается на всех локализованных версиях поддерживаемых операционных систем. Локализованные версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются в локализованных операционных системах на том же языке, что и локализованная версия собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Локализованные версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также поддерживаются английскими версиями операционных систем, если установлены совпадающие языковые настройки.  
  
 Для обновлений.  
  
-   Английские версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно обновить до любой локализованной версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Локализованные версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно обновить до локализованных версий собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на том же языке.  
  
-   Локализованную версию собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно обновить до английской версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Локализованные версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нельзя обновить до локализованных версий собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другом языке.  
  
## <a name="data-type-compatibility-for-client-versions"></a>Совместимость типов данных для версий клиента  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставляют новые типы данных со старыми, которые совместимы с клиентами низкого уровня, как показано в таблице ниже.  
  
 Приложения OLE DB и ADO могут использовать ключевое слово [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] строки подключения **DataTypeCompatibility** с Native Client для работы со старыми типами данных. При использовании **DataTypeCompatibility=80** клиенты OLE DB соединятся с помощью версии потока табличных данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], а не потока табличных данных. Это значит, что для [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних типов данных преобразование низкого уровня будет выполнено сервером, а не собственным клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это также означает, что функции, доступные при соединении, будут ограничиваться набором функций [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Попытки использовать новые типы данных или функций быстро определяются по вызовам API-интерфейса и ошибкам, возвращаемым вызывающему приложению, а не по попыткам передать недопустимые запросы на сервер.  
  
 Для ODBC нет контроля **совместимости DataType Compatibility.**  
  
 IDBInfo::GetKeywords всегда будет возвращать список ключевых слов, соответствующий версии сервера при соединении и не затронутый **DataTypeCompatibility**.  
  
|Тип данных|собственный клиент SQL Server<br /><br /> SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Компоненты доступа к данным Windows, компоненты MDAC и<br /><br /> приложения OLE DB собственного клиента SQL Server со свойством DataTypeCompatibility=80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8 КБ)|определяемый пользователем тип|Udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|Образ —|  
|varchar(max)|varchar|varchar|Text|  
|nvarchar(max)|nvarchar|nvarchar|Ntext|  
|Xml|Xml|Xml|Ntext|  
|CLR UDT (> 8Kb)|определяемый пользователем тип|varbinary|Образ —|  
|Дата|Дата|varchar|Varchar|  
|datetime2|datetime2|varchar|Varchar|  
|datetimeoffset|datetimeoffset|varchar|Varchar|  
|time|time|varchar|Varchar|  
  
## <a name="see-also"></a>См. также:  
 [Программирование коренных клиентов сервера S'L](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Установка собственного клиента SQL Server](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
  
  
