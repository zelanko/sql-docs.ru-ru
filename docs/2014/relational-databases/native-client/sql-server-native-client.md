---
title: Новые&#39;в SQL Server Native Client | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 003abb67cd66d02294210ddb3f55061abcc804f4
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704146"
---
# <a name="what39s-new-in-sql-server-native-client"></a>Новые&#39;в SQL Server Native Client
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] устанавливает [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client. [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Native Client отсутствует.  
  
 Других обновлений для драйвера ODBC в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client не будет. Преемник драйвера ODBC в клиенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, называемый драйвером [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC Driver 11 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Windows, устанавливается вместе с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Дополнительные сведения о [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC Driver 11 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Windows см. в разделе [Microsoft ODBC Driver 11 для SQL Server — Windows](https://www.microsoft.com/download/details.aspx?id=36434).  
  
 Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в последний раз был обновлен в собственном клиенте [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] . Разработчики, желающие использовать поставщик OLE DB для подключения к последней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должны будут применять поставщик OLE DB из состава [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client.  
  
 В следующем разделе описаны новые важные функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]Native Client.  
  
-   [Поддержка SQL Server Native Client для LocalDB](features/sql-server-native-client-support-for-localdb.md)  
  
-   [Обнаружение метаданных](features/metadata-discovery.md)  
  
-   [Поддержка UTF-16 в собственном клиенте SQL Server версии 11.0](features/utf-16-support-in-sql-server-native-client-11-0.md)  
  
-   [Поддержка высокого уровня доступности и аварийного восстановления собственного клиента SQL Server](features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [Доступ к диагностическим сведениям в журнале расширенных событий](features/accessing-diagnostic-information-in-the-extended-events-log.md)  
  
 Кроме того, теперь драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает три функции, добавленные в стандарт ODBC в пакете Windows 7 SDK.  
  
-   Асинхронное выполнение операций, связанных с соединением. Дополнительные сведения см. в разделе [Асинхронное выполнение](https://go.microsoft.com/fwlink/?LinkID=191493).  
  
-   Возможность расширения типа данных C. Дополнительные сведения о типах данных см. в разделе [Типы данных C в ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).  
  
     Для поддержки этой функции в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственном клиенте SQLGetDescField может возвращать `SQL_C_SS_TIME2` (для `time` типов) или `SQL_C_SS_TIMESTAMPOFFSET` (для `datetimeoffset` ), а не `SQL_C_BINARY` , если приложение использует ODBC 3,8. Дополнительные сведения см. в разделе [Поддержка типов данных для улучшений даты и времени ODBC](features/date-and-time-improvements.md).  
  
-   Многократный вызов метода `SQLGetData` с небольшим буфером для получения значения параметра большого объема. Дополнительные сведения см. в разделе [Получение выходных параметров с помощью метода SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).  
  
 В следующих разделах описываются изменения поведения собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   При вызове `ICommandWithParameters::SetParameterInfo` значение, передаваемое в параметр *pwszName* , должно быть допустимым идентификатором. Дополнительные сведения см. в разделе [ICommandWithParameters](../native-client-ole-db-interfaces/icommandwithparameters.md).  
  
-   Функция `SQLDescribeParam` теперь постоянно возвращает значение, соответствующее спецификации ODBC. Дополнительные сведения см. в разделе [SQLDescribeParam](../native-client-odbc-api/sqldescribeparam.md).  
  
-   [Изменение поведения драйвера ODBC при обработке преобразования символов](features/odbc-driver-behavior-change-when-handling-character-conversions.md)  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](features/sql-server-native-client-features.md)  
  
  
