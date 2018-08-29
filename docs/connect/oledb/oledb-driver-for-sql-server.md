---
title: Драйвер OLE DB для SQL Server | Документы Майкрософт
description: Драйвер Microsoft OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb
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
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 3e1764fdd2a96fcf1d0da218ef86b2e4cb62fd8c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025915"
---
# <a name="microsoft-ole-db-driver-for-sql-server"></a>Драйвер Microsoft OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server является отдельной доступа прикладной программный интерфейс (API), используемый для OLE DB, которая была введена в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Драйвер OLE DB для SQL Server обеспечивает драйвер OLE DB для SQL в одной библиотеке динамической компоновки (DLL). Также он предоставляет новые расширенные функциональные возможности, поставляемые компонентами доступа к данным Windows (выделенное административное соединение Windows, ранее — компоненты доступа к данным компонентов MDAC). Драйвер OLE DB для SQL Server может применяться для создания новых или усовершенствования существующих приложений, которым требуется доступ к новым функциям [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], таким как множественный активный результирующий набор (MARS), пользовательские типы, уведомления о запросах, изоляция моментальных снимков и поддержка типа данных XML.  
  
> [!NOTE]  
>  Список различий между драйвер OLE DB для SQL Server и Windows DAC плюс сведения о проблемах, которые следует учесть перед обновлением приложения Windows DAC для драйвера OLE DB для SQL Server, см. в разделе [обновление приложения для драйвера OLE DB для SQL Server с компонентами MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
 Драйвер OLE DB для SQL Server может использоваться совместно с основными службами OLE DB, поставляемыми с компонентами доступа к данным Windows DAC, но это не является обязательным требованием. Выбор того, использовать или нет основные службы, зависит от требований отдельного приложения (например, требуется ли пул соединений).  
  
 Приложения объектов данных ActiveX (ADO), могут использовать драйвер OLE DB для SQL Server, но рекомендуется использовать ADO совместно с **DataTypeCompatibility** ключевое слово строки подключения (или с соответствующим  **Источник данных** свойство). При использовании драйвера OLE DB для SQL Server, приложения ADO могут использовать эти новые функции, представленные в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , которые доступны через драйвер OLE DB для SQL Server с помощью ключевых слов строки подключения или свойства OLE DB или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Дополнительные сведения об использовании этих функций с ADO см. в разделе [использование объектов ADO с драйвер OLE DB для SQL Server](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
 Драйвер OLE DB для SQL Server призван обеспечить упрощенный собственный доступ к данным SQL Server через OLE DB. Он позволяет внедрять и развивать новые функции доступа к данным без изменения текущих компонентов Windows DAC, которые теперь являются частью платформы Microsoft Windows.  
  
 Драйвер OLE DB для SQL Server использует компоненты доступа к данным Windows DAC, однако явно не зависит от их конкретных версий. Можно использовать драйвер OLE DB для SQL Server с версией Windows DAC, который устанавливается вместе с любой операционной системе, поддерживаемых драйвером OLE DB для SQL Server.  

 ## <a name="different-generations-of-ole-db-drivers"></a>Разных поколений драйверы OLE DB

Существует три поколения различных поставщиков Microsoft OLE DB для SQL Server.

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Поставщик Microsoft OLE DB для SQL Server (SQLOLEDB)
[Поставщик Microsoft OLE DB для SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB), по-прежнему поставляется как часть [Windows Data Access Components](https://msdn.microsoft.com/library/ms692897.aspx). Больше не поддерживается и не рекомендуется использовать этот драйвер для разработки новых приложений.

### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)
Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) включает интерфейс поставщика OLE DB (SQLNCLI) и поставщик OLE DB, которая поставлялась с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] через [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].

Это было [, устаревшие в 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) и не рекомендуется использовать этот драйвер для разработки новых приложений. Дополнительные сведения о жизненном цикле SNAC и доступных файлов для загрузки см. [жизненного цикла SNAC описано](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Драйвер Microsoft OLE DB для SQL Server (MSOLEDBSQL)
OLE DB не [undeprecated](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) и выпущенная в 2018 г.

Новый поставщик OLE DB, называется драйвера Microsoft OLE DB для SQL Server (MSOLEDBSQL). Новый поставщик будет обновляться последние функции сервера, в дальнейшем.

> [!NOTE]
> Чтобы использовать новый драйвер OLE DB Майкрософт для SQL Server в существующие приложения, необходимо запланировать для преобразования строки подключения из SQLOLEDB и SQLNCLI, MSOLEDBSQL.
  
## <a name="in-this-section"></a>в этом разделе  
[Когда использовать драйвер OLE DB для SQL Server](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 Обсуждается место драйвера OLE DB для SQL Server среди технологий доступа к данным корпорации Майкрософт, дается его сравнение с компонентами доступа к данным Windows DAC и ADO.NET, а также предоставляются указания, помогающие решить, какую технологию доступа к данным следует использовать.  
  
 [Возможности драйвера OLE DB для SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  
 Описание возможностей, поддерживаемых драйвером OLE DB для SQL Server.  
  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 Представлены общие сведения о разработке с помощью драйвера OLE DB для SQL Server, включая отличия от компонентов доступа к данным Windows DAC, используемые компоненты и способ использования совместно с ADO.  
  
 В этом разделе также рассматриваются драйвера OLE DB для установки SQL Server и развертывания, включая способ распространения драйвера OLE DB для SQL Server библиотеки.  
  
 [Системные требования драйвера OLE DB для SQL Server](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 Обсуждаются системные ресурсы, необходимые для использования драйвера OLE DB для SQL Server.  
  
 [Программирование драйвера OLE DB для SQL Server](../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
 Сведения об использовании драйвера OLE DB для SQL Server.  
  
 [Дополнительные сведения о драйвере OLE DB для SQL Server](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 Предоставляет дополнительные ресурсы о драйвере OLE DB для SQL Server, включая ссылки на внешние ресурсы и получение дальнейшей помощи.  
  
  
## <a name="see-also"></a>См. также:  
 [Обновление приложения с переходом от SQL Server 2005 Native Client](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [Инструкции по OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
