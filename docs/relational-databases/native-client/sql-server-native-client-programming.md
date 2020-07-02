---
title: Программирование
description: Используйте эти ресурсы, чтобы понять SQL Server Native Client, автономный API доступа к данным, используемый как для OLE DB, так и для ODBC.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, about SQL Server Native Client
- SQL Server Native Client, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
- data access [SQL Server Native Client]
- SQL Server Native Client
- SQLNCLI
- native data access [SQL Server Native Client]
ms.assetid: 14ba2cb1-a424-4e4d-b224-0bf1015ab801
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ee461de8a6039716a287605de5268c127b76ec3e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787604"
---
# <a name="sql-server-native-client-programming"></a>Программирование собственного клиента SQL Server
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — это изолированный прикладной программный интерфейс (API) для доступа к данным, используемый в OLE DB и ODBC, который появился в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объединяет поставщика SQL OLE DB и драйвер SQL ODBC в одну собственную DLL-библиотеку. Также он предоставляет новые расширенные функциональные возможности, поставляемые компонентами доступа к данным Windows (выделенное административное соединение Windows, ранее — компоненты доступа к данным компонентов MDAC). Технология собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может применяться для создания новых или усовершенствования существующих приложений, которым требуется доступ к новым функциям [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], таким как режим MARS, определяемые пользователем типы, уведомления о запросах, изоляция моментальных снимков и поддержка типа данных XML.  
  
> [!NOTE]  
>  Список различий между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственным клиентом и приложением Windows DAC, а также сведения о проблемах, которые следует учитывать перед обновлением приложения DAC для Windows до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента, см. в разделе [обновление приложения для SQL Server Native Client из MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
 Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда используется совместно с диспетчером драйверов ODBC, поставляемым с выделенным административным соединением Windows. Поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может использоваться совместно с основными службами OLE DB, поставляемыми с выделенным административным соединением Windows, но это не является обязательным требованием. Выбор того, использовать или нет основные службы, зависит от требований отдельного приложения (например, требуется ли пул соединений).  
  
 Приложения ActiveX Data Object (ADO) могут использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный поставщик OLE DB клиента, но рекомендуется использовать ADO совместно с ключевым словом строки подключения **DataTypeCompatibility диспетчера соединений** (или соответствующим свойством **DataSource** ). При использовании поставщика OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложения ADO могут использовать новые функции [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], доступные в собственном клиенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], через ключевые слова строки соединения, свойства OLE DB или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Дополнительные сведения об использовании этих функций с ADO см. в разделе [Использование ADO с SQL Server Native Client](../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md).  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] призван обеспечить упрощенный собственный доступ к данным SQL Server через OLE DB и ODBC. Упрощение состоит в том, что он сочетает в единой библиотеке технологии OLE DB и ODBC и позволяет внедрять и развивать новые функции доступа к данным без изменения текущих компонентов выделенного административного соединения Windows, которые теперь являются частью платформы Microsoft Windows.  
  
 Хотя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент использует компоненты приложения Windows DAC, он не зависит явно от конкретной версии приложения уровня данных Windows. Собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать с версией выделенного административного соединения Windows, которая устанавливается с любой операционной системой, поддерживаемой собственным клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [собственный клиент SQL Server](../../relational-databases/native-client/sql-server-native-client.md)  
 Предоставляет список наиболее значительных новых функциональных возможностей Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Когда использовать собственный клиент SQL Server](../../relational-databases/native-client/when-to-use-sql-server-native-client.md)  
 Обсуждается место собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] среди технологий доступа к данным корпорации Майкрософт, дается его сравнение с выделенным административным соединением Windows и ADO.NET, и предоставляются указатели, помогающие решить, какую технологию доступа к данным следует использовать.  
  
 [Компоненты собственного клиента SQL Server](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
 Описываются функции, поддерживаемые собственным клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Построение приложений с использованием SQL Server Native Client](../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
 Представлены общие сведения о разработке с помощью собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая отличия от Windows DAC, используемые компоненты и способ использования совместно с ADO.  
  
 В этом разделе также обсуждается установка и развертывание собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая способ распространения библиотеки собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Системные требования для собственного клиента SQL Server](../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
 Обсуждаются системные ресурсы, необходимые для использования с собственным клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
 Предоставляются сведения об использовании поставщика OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
 Предоставляются сведения об использовании драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Поиск дополнительных сведений о собственном клиенте SQL Server](../../relational-databases/native-client/finding-more-sql-server-native-client-information.md)  
 Предоставляются дополнительные ресурсы о собственном клиенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая ссылки на внешние ресурсы и получение дальнейшей помощи.  
  
 [Ошибки собственного клиента SQL Server](https://msdn.microsoft.com/library/ebd0e9a8-5fe5-4b15-9a44-2f131a13c186)  
 Содержит разделы об ошибках времени выполнения, связанных с собственным клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Обновление приложения с SQL Server 2005 Native Client](../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md)   
 [Разделы руководства по ODBC](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Инструкции по OLE DB](../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
