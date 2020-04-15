---
title: Политики поддержки для родного клиента сервера S'L (ru) Документы Майкрософт
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 09c80cf4-23e6-4027-a24f-cdb9c87af811
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4dd81e9d23be08a617cefe9cf756feb83040c11c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288137"
---
# <a name="support-policies-for-sql-server-native-client"></a>Политики поддержки собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этом разделе рассматриваются способы использования различных компонентов доступа к данным с собственным клиентом Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="server-support"></a>Поддержка сервера  
 Клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 поддерживает соединение с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] и [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
## <a name="supported-operating-system-versions"></a>Поддерживаемые версии операционных систем  
 В следующей таблице приведен список операционных систем, поддерживающих Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
|Версия собственного клиента SQL Server|Поддерживаемые операционные системы|  
|--------------------------------------|---------------------------------|  
|Собственный клиент SQL Server (SQL Server 2005)|Microsoft Windows 2000 с пакетом обновления 4 (SP4) или более поздней версии<br /><br /> Microsoft Windows Server 2003 или более поздней версии<br /><br /> Microsoft Windows XP Service Pack 1 или более поздний<br /><br /> Microsoft Windows Vista (требуется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с пакетом обновления 2 (SP2) или более поздней версии)<br /><br /> Microsoft Windows Server 2008 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] R2 (требует пакет услуг 2 или позже)|  
|СЗЛ Сервер Родной Клиент[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]10.0 ( )|Microsoft Windows Server 2003 с пакетом обновления 2 (SP2) или более поздней версии<br /><br /> Microsoft Windows XP с пакетом обновления 2 (SP2) или более поздней версии<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2|  
|СЗЛ Сервер Родной Клиент[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]10.5 ( )|Microsoft Windows Server 2003 с пакетом обновления 2 (SP2) или более поздней версии<br /><br /> Microsoft Windows XP с пакетом обновления 2 (SP2) или более поздней версии<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7|  
|Клиент SQL Server Native Client 11.0 ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] и [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)])|Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7<br /><br /> Microsoft Windows 8<br /><br /> Microsoft Windows Server 2012|  
  
## <a name="ado-support-policies"></a>Политика поддержки ADO  
 Приложение ADO может пользоваться поставщиком OLE DB SQLOLEDB, который входит в состав Windows, если ему не требуются функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии.  
  
 Приложения ADO могут использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версию [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]Native Client, включенную в . Приложения ADO могут также пользоваться собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 11.0 (в составе [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]), но в этом случае необходимо указать `DataTypeCompatibility=80` в строке соединения. Только функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] будут доступны, если в строке соединения указано значение `DataTypeCompatibility=80`.  
  
## <a name="bcp-support-policies"></a>Политика поддержки BCP  
 Начиная с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], программа bcp.exe поддерживает файлы данных, которые не более чем на три версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] старше версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], с которой поставляется экземпляр bcp.exe.  
  
## <a name="odbc-support-policies"></a>Политика поддержки ODBC  
 Приложения должны пользоваться драйвером ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], включенным в операционную систему Windows. Если приложение сертифицировано для работы с определенной версией собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то можно пользоваться драйвером ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="ole-db-support-policies"></a>Политики поддержки OLE DB  
 Приложения должны пользоваться поставщиком OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], включенным в операционную систему Windows. Если приложение сертифицировано для работы с определенной версией собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то можно пользоваться поставщиком собственного клиента OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Приложение OLE DB, которое не было сертифицированы для использования с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], может пользоваться собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], если в его строке соединения указано `DataTypeCompatibility=80`.  
  
 Приложение OLE DB, которое пользуется компонентом службы OLE DB, может пользоваться собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], если в строке соединения указано `DataTypeCompatibility=80`. Однако в этом [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] случае не будут доступны функции, добавленные после этого.  
  
## <a name="see-also"></a>См. также:  
 [Построение приложений с использованием собственного клиента SQL Server](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
