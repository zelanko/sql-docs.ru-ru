---
title: Драйвер OLE DB для SQL Server | Документы Microsoft
description: Драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: OLE DB Driver
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server
- MSOLEDBSQL
- native data access [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 7aef3dc362cfd83d1767f759b30cddde263d319f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-driver-for-sql-server"></a>Драйвер OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server — данных автономного доступа прикладной программный интерфейс (API) используется для OLE DB, которая была введена в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Драйвер OLE DB для SQL Server обеспечивает драйвер OLE DB для SQL в одной библиотеке динамической компоновки (DLL). Также он предоставляет новые расширенные функциональные возможности, поставляемые компонентами доступа к данным Windows (выделенное административное соединение Windows, ранее — компоненты доступа к данным компонентов MDAC). Драйвер OLE DB для SQL Server может использоваться для создания новых или усовершенствования существующих приложений, которые необходимо воспользоваться преимуществами функций, появившихся в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], такие как несколько активных результирующих наборов (MARS), данных, определяемых пользователем типов (UDT), запрос поддерживает уведомления, изоляция моментальных снимков и тип данных XML.  
  
> [!NOTE]  
>  Список различий между драйвер OLE DB для SQL Server и Windows DAC, а также сведения о проблемах учесть перед обновлением приложения Windows DAC до драйвер OLE DB для SQL Server см. в разделе [обновление приложения для драйвера OLE DB для SQL Сервер с компонентами MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
 Драйвер OLE DB для SQL Server можно использовать в сочетании с основными службами OLE DB вместе с выделенным административным Соединением Windows, но это не является обязательным; по желанию могут использовать основные службы, или не зависит от требований отдельного приложения (например, если организация пулов соединений не требуется).  
  
 Приложения объектов данных ActiveX (ADO), могут использовать драйвер OLE DB для SQL Server, но рекомендуется использовать ADO совместно с **DataTypeCompatibility** ключевое слово строки подключения (или с соответствующим  **Источник данных** свойство). При использовании драйвера OLE DB для SQL Server, приложения ADO могут использовать новые функции в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , можно загрузить через драйвер OLE DB для SQL Server с помощью ключевых слов строки подключения или свойства OLE DB или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Дополнительные сведения об использовании этих функций с ADO см. в разделе [с помощью ADO с драйвер OLE DB для SQL Server](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
 Драйвер OLE DB для SQL Server была разработана для предоставления упрощенного доступа к данным собственного SQL Server с помощью OLE DB. Он позволяет внедрять и развивать новые функции доступа к данным без изменения текущих компонентов выделенного административного Соединения Windows, которые теперь являются частью платформы Microsoft Windows.  
  
 Драйвер OLE DB для SQL Server использует компоненты выделенного административного соединения Windows, но не явно зависит от конкретной версии Windows DAC. Драйвер OLE DB для SQL Server можно использовать с версией выделенного административного соединения Windows, которая устанавливается с любой операционной системе, поддерживаемых драйвером OLE DB для SQL Server.  

 ## <a name="different-generations-of-ole-db-drivers"></a>Разных поколений драйверы OLE DB

Существует три поколения различных поставщиков Microsoft OLE DB для SQL Server.

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Поставщик Microsoft OLE DB для SQL Server (SQLOLEDB)
[Поставщик Microsoft OLE DB для SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB), по-прежнему поставляется как часть [компоненты доступа к данным Windows](https://msdn.microsoft.com/en-us/library/ms692897.aspx). Больше не поддерживается и не рекомендуется использовать этот драйвер для разработки новых приложений.

### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)
Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) включает интерфейс поставщика OLE DB (SQLNCLI) и поставщика OLE DB, которая поставлялась с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] через [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].

Это было [устаревшие в 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) и не рекомендуется использовать этот драйвер для разработки новых приложений. Дополнительные сведения о SNAC жизненный цикл и программ для загрузки см. [жизненного цикла SNAC описано](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Драйвер Microsoft OLE DB для SQL Server (MSOLEDBSQL)
OLE DB не [undeprecated](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) и выпущенные 2018.

Новый поставщик OLE DB, называется драйвер Microsoft OLE DB для SQL Server (MSOLEDBSQL). Новый поставщик будет добавлено в последние функции сервера Забегая вперед.

> [!NOTE]
> Чтобы использовать новый Microsoft OLE DB драйвер для SQL Server в существующих приложениях, следует запланировать для преобразования строки подключения из SQLOLEDB и SQLNCLI, MSOLEDBSQL.
  
## <a name="in-this-section"></a>В этом разделе  
[Когда использовать драйвер OLE DB для SQL Server](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 Обсуждается, как драйвер OLE DB для SQL Server сочетается с данным технологий доступа, как его сравнение с выделенным административным Соединением Windows и ADO.NET и предоставляет указатели, помогающие решить которых технологии доступа к данным.  
  
 [Возможности драйвера OLE DB для SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  
 Описание возможностей, поддерживаемых драйвером OLE DB для SQL Server.  
  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 Обзор драйвер OLE DB для SQL Server разработки, включая отличия от Windows DAC, компоненты, которые он использует, и о том, как можно использовать ADO с ним.  
  
 В этом разделе также рассматриваются драйвер OLE DB для установки SQL Server и развертывания, включая способ распространения драйвер OLE DB для SQL Server библиотеки.  
  
 [Системные требования драйвера OLE DB для SQL Server](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 Обсуждаются системные ресурсы, необходимые для использования драйвера OLE DB для SQL Server.  
  
 [Программирование драйвера OLE DB для SQL Server](../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
 Предоставляет сведения об использовании драйвера OLE DB для SQL Server.  
  
 [Дополнительные сведения о драйвере OLE DB для SQL Server](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 Предоставляет дополнительные ресурсы, посвященные драйвер OLE DB для SQL Server, включая ссылки на внешние ресурсы и получение дальнейшей помощи.  
  
  
## <a name="see-also"></a>См. также  
 [Обновление приложения от собственного клиента SQL Server 2005](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [Разделы руководства по OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
