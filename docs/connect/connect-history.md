---
title: История драйверов для Microsoft SQL Server | Документация Майкрософт
description: На этой странице описываются все технологии Майкрософт для подключения к данным на сервере SQL Server.
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f5db99b78cc5c5d251baee6028d1c9bc4e7448bf
ms.sourcegitcommit: fb1430aedbb91b55b92f07934e9b9bdfbbd2b0c5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2020
ms.locfileid: "82885771"
---
# <a name="driver-history-for-microsoft-sql-server"></a>История драйверов для Microsoft SQL Server

На этой странице описываются все технологии Майкрософт для подключения к данным на сервере SQL Server.

## <a name="odbc"></a>ODBC

Есть три поколения Microsoft ODBC Driver for SQL Server. Первый драйвер ODBC "SQL Server" по-прежнему входит в состав [компонентов доступа к данным Windows DAC](#microsoft-or-windows-data-access-components). Использовать этот драйвер при разработке новых продуктов не рекомендуется. Начиная с SQL Server 2005 [SQL Server Native Client](#sql-server-native-client) содержит интерфейс ODBC и драйвер ODBC, поставляемый в составе версий от SQL Server 2005 до версии SQL Server 2012. Использовать этот драйвер при разработке новых продуктов не рекомендуется. После SQL Server 2012 появился драйвер [Microsoft ODBC Driver for SQL Server](#microsoft-odbc-driver-for-sql-server). Именно в него добавляются все новые серверные возможности и компоненты.

### <a name="sql-server-native-client"></a>собственный клиент SQL Server

SQL Server Native Client — это изолированная библиотека, которая используется как для OLE DB, так и для ODBC. SQL Server Native Client (SNAC) входил в состав с SQL Server 2005 по SQL Server 2012. SQL Server Native Client можно использовать для приложений, которым нужны новые возможности, появившиеся в версиях с SQL Server 2005 до SQL Server 2012. (Компоненты доступа к данным Microsoft/Windows не обновляются для этих новых функций в SQL Server.) Для новых возможностей, введенных после SQL Server 2012, SQL Server Native Client обновляться не будет. Если вам нужны новые возможности SQL Server, переходите на Microsoft ODBC Driver for SQL Server или Microsoft OLE DB для SQL Server.

Полное описание SQL Server Native Client см. в [документации SQL Server Native Client](../relational-databases/native-client/sql-server-native-client-programming.md).

### <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server

После SQL Server 2012 основной драйвер ODBC для SQL Server разрабатывается и выпускается как Microsoft ODBC Driver for SQL Server. Дополнительные сведения см. в [документации Microsoft ODBC Driver for SQL Server](./odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="ole-db"></a>OLE DB

Существует три поколения поставщиков Microsoft OLE DB для SQL Server. Microsoft OLE DB Provider for SQL Server (SQLOLEDB) по-прежнему поставляется в составе [компонентов доступа к данным Windows](#microsoft-or-windows-data-access-components). В этот поставщик не будут добавляться новые возможности, и его не рекомендуется использовать при разработке новых продуктов. Начиная с SQL Server 2005 [SQL Server Native Client](#sql-server-native-client) содержит интерфейс поставщика OLE DB (SQLNCLI) и является поставщиком OLE DB, который поставляется в версиях с SQL Server 2005 по SQL Server 2017. [С 2011 года он считается устаревшими](/archive/blogs/sqlnativeclient/microsoft-is-aligning-with-odbc-for-native-relational-data-access) и мы не рекомендуем использовать этот драйвер для разработки новых приложений. В 2017 году технология доступа к данным OLE DB была снова [объявлена рекомендуемой и на 2018 год был запланирован новый выпуск ](/archive/blogs/sqlnativeclient/announcing-the-new-release-of-ole-db-driver-for-sql-server). Новый поставщик OLE DB называется Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL) и именно он поддерживается в настоящее время.

## <a name="adonet"></a>ADO.NET

ADO.NET впервые появился в составе платформы Microsoft.NET. Этот компонент поддерживается и постоянно улучшается и по сей день. Это основной компонент платформы Microsoft .NET Framework. Дополнительные сведения см. в статье [Microsoft ADO.NET for SQL Server](ado-net/microsoft-ado-net-sql-server.md) (Microsoft ADO.NET для SQL Server).

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>Microsoft JDBC Driver для SQL Server

Выпущенный в 2000 году драйвер Microsoft JDBC для SQL Server поддерживается и постоянно улучшается и по сей день. Исходный код этого драйвера был открыт в 2016 году. Актуальные сведения, в том числе сведения о загрузке драйвера, см. в статье [Общие сведения о драйвере JDBC](./jdbc/overview-of-the-jdbc-driver.md).

## <a name="php"></a>PHP

### <a name="microsoft-drivers-for-php-for-sql-server"></a>Драйверы Microsoft SQL Server для PHP

Выпущенные в 2009 году в составе проекта с открытым исходным кодом драйверы Microsoft SQL Server для PHP поддерживаются и постоянно улучшаются и по сей день. Актуальные сведения, в том числе сведения о загрузке драйвера для PHP, см. в статье [Драйверы Microsoft SQL Server для PHP](./php/microsoft-php-driver-for-sql-server.md).

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>Драйвер Microsoft SQL Server для Node.js

Драйвер Microsoft SQL Server для Node.js позволяет приложениям Node.js в Microsoft Windows и Microsoft Azure получать доступ к Microsoft SQL Server и базе данных SQL Microsoft Azure. Дальнейшая разработка этого драйвера больше не ведется. Создавать новые приложения с помощью драйвера Microsoft SQL Server для Node.js не рекомендуется.

Дополнительные сведения о драйвере Microsoft SQL Server для Node.js см. [здесь](https://github.com/Azure/node-sqlserver).

### <a name="tedious"></a>Tedious

Сейчас Майкрософт поддерживает и помогает развивать модуль с открытым исходным кодом Tedious в Node.js. Этот модуль используется для подключения к SQL Server с помощью JavaScript. Дополнительные сведения см. в статье [Драйвер Node.js для SQL Server](./node-js/node-js-driver-for-sql-server.md).

## <a name="microsoft-or-windows-data-access-components"></a>Компоненты доступа к данным Microsoft или Windows

Компоненты доступа к данным Microsoft/Windows (MDAC/WDAC) поставляются вместе с Windows. Они обеспечивают обратную совместимость приложений, но не входят в текущий стек технологий SQL Server. Новые возможности в компоненты MDAC/WDAC добавляться не будут, и их не рекомендуется использовать для разработки новых приложений.

В этом документе стек MDAC/WDAC можно разделить на следующие компоненты с точки зрения технологий и продуктов:

* **ADO** (в том числе ADOMD и ADOX);
* **OLE DB** (в том числе основные службы OLE DB, поставщик OLE DB для SQL Server, поставщик OLE DB для Oracle, поставщик OLE DB для драйверов ODBC, поставщик Data Shape Provider и поставщик удаленных данных);
* **ODBC** (в том числе диспетчер драйверов ODBC, драйвер для SQL ODBC и драйвер для Oracle ODBC).

### <a name="mdacwdac-components"></a>Компоненты MDAC/WDAC

MDAC/WDAC содержит следующие компоненты:

* **ODBC**. Microsoft Open Database Connectivity (ODBC) — это интерфейс языка программирования C, позволяющий приложениям получать доступ к данным из различных систем управления базами данных (СУБД). Приложения, использующие этот API-интерфейс, ограничены только доступом к реляционным источникам данных.
* **OLE DB**. OLE DB — это набор COM-интерфейсов для доступа к данным в различных хранилищах данных. Поставщики OLE DB дают возможность работать с данными в базах данных, файловых системах, хранилищах сообщений, службах каталогов, рабочих процессах и хранилищах документов.
* **ADO**. Объекты данных ActiveX (ADO) предоставляют модель программирования высокого уровня. Несмотря на то, что ADO дает чуть меньшую производительность, чем код для OLE DB или ODBC, ADO легко освоить и использовать. Этот компонент можно использовать в языках сценариев, таких как Microsoft Visual Basic Scripting Edition (VBScript) или Microsoft JScript.
* **ADOMD**. ADO многомерных данных (ADOMD) используется с поставщиками многомерных данных, такими как поставщик Microsoft OLAP, также известный как поставщик Microsoft Analysis Services. С момента выпуска MDAC 2.0 существенные улучшения в компонент не вносились.
* **ADOX**. Расширения ADO для языка DDL и безопасности (ADOX) позволяют создавать и изменять определения баз данных, таблиц, индексов или хранимых процедур. ADOX можно использовать с любым поставщиком. Поставщик OLE DB для Microsoft Jet обеспечивает полную поддержку ADOX, а поставщик OLE DB для Microsoft SQL Server предоставляет ограниченную поддержку.
* **Сетевые библиотеки Microsoft SQL Server**. Сетевые библиотеки SQL Server позволяют SQLOLEDB и SQLODBC взаимодействовать с базой данных SQL Server. В выпусках MDAC/WDAC объявлены нерекомендуемыми следующие сетевые библиотеки SQL Server: Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet и RPC. TCP/IP и именованные каналы будут по-прежнему поддерживаться. Кроме того, они доступны в 64-разрядной ОС Windows.
* **MSDASQL**. Поставщик Microsoft OLE DB для ODBC (MSDASQL) позволяет приложениям, созданным с использованием OLE DB и ADO (в которых используется OLEDB) обращаться к источникам данных через драйвер ODBC. MSDASQL — это поставщик OLEDB, который подключается к ODBC, а не к базе данных. Он выступает в роли моста между OLE DB и драйвером ODBC, если для источника данных не существует прямого поставщика OLE DB. MSDASQL поставляется с операционной системой Windows. Первыми выпусками Windows, содержащими 64-разрядную версию технологии, были Windows Server 2008 и Vista с пакетом обновления 1 (SP1).

### <a name="deprecated-mdacwdac-components"></a>Нерекомендуемые компоненты MDAC/WDAC

Эти компоненты по-прежнему поддерживаются в текущем выпуске MDAC/WDAC, но в будущих выпусках они могут быть удалены. Майкрософт рекомендует не использовать эти компоненты при разработке новых приложений. Кроме того, при обновлении или изменении существующих приложений удалите все зависимости от этих компонентов.

* **SQLOLEDB**. Поставщик Microsoft OLE DB для SQL Server (SQLOLEDB), который поддерживает доступ к Microsoft SQL Server, объявлен нерекомендуемым. Возможность подключения к будущим версиям SQL Server не гарантируется. Возможность подключения к версиям, предшествующим SQL Server 7, будет удалена из операционных систем, вышедшим после Windows 7. Новые приложения должны использовать драйвер Microsoft OLE DB для SQL Server (MSOLEDBSQL), который поддерживает новые возможности SQL Server. Существующие приложения нужно перевести на драйвер Microsoft OLE DB для SQL Server, чтобы улучшить производительность, надежность и возможности поддержки. Дополнительные сведения см. в статье [Updating an Application to OLE DB Driver for SQL Server from MDAC](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md) (Обновление приложения с переходом с MDAC на драйвер OLE DB для SQL Server).
* **SQLODBC**. Драйвер Microsoft ODBC для SQL Server (SQLODBC), который поддерживает доступ к Microsoft SQL Server, объявлен нерекомендуемым. Возможность подключения к будущим версиям SQL Server не гарантируется. Возможность подключения к версиям, предшествующим SQL Server 7, будет удалена из операционных систем, вышедшим после Windows 7. Новые приложения должны использовать Microsoft ODBC Driver for SQL Server в Windows, который поддерживает новые возможности SQL Server. Существующие приложения нужно перевести на драйвер Microsoft ODBC Driver for SQL Server, чтобы улучшить производительность, надежность и возможности поддержки. Соответствующие сведения см. в статье [Updating an Application to SQL Server Native Client from MDAC](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md) (Обновление приложения с переходом с MDAC на SQL Server Native Client).
* **Microsoft Jet Database Engine 4.0**. Начиная с версии 2.6 MDAC больше не содержит компоненты Jet. Другими словами, MDAC 2.6, 2.7 и 2.8 не содержат Microsoft Jet, поставщик OLE DB для Microsoft Jet, драйверы базы данных ODBC для настольных систем и объекты Jet Data Access Objects (DAO). 

  64-разрядные версии ядра СУБД Jet, драйвера Jet OLEDB, драйвера Jet ODBC и Jet DAO не существуют. Дополнительные сведения см. в [статье базы знаний 957570](https://support.microsoft.com/kb/957570). В 64-разрядных версиях Windows 32-разрядная версия Jet выполняется в подсистеме Windows WOW64. Дополнительные сведения о WOW64 см. в разделе [Документация MSDN по WOW64](/windows/desktop/WinProg64/wow64-implementation-details). Нативные 64-разрядные приложения не могут взаимодействовать с 32-разрядными драйверами Jet, работающими в WOW64.

  Для разработки новых приложений, которые не используют Microsoft Access и которым требуется реляционное хранилище данных, вместо Microsoft Jet мы рекомендуем использовать [Microsoft SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express). Эти новые или преобразованные приложения могут продолжать использовать Jet с целью использования файлов Microsoft Office 2003 и более ранних версий (MDB и XLS) для неосновного хранилища данных. Однако для этих приложений следует запланировать переход с Jet на ядро СУБД Microsoft Access. Можно [загрузить ядро СУБД Microsoft Access](https://www.microsoft.com/download/details.aspx?id=54920), которое позволяет выполнять чтение и запись существующих файлов в формате Office 2003 (MDB и XLS) или Office 2007 (ACCDB, XLSM, XLSX и XLSB).

  > [!IMPORTANT]
  > Ознакомьтесь с лицензионным соглашением для конечных пользователей системы Office 2007 на предмет особых ограничений использования.

  > [!NOTE]
  > Приложения SQL Server также могут получить доступ к файлам системы Office 2007 и более ранней версии из подключений к разнородным данным SQL Server и возможностей служб интеграции, с помощью драйвера системы Office 2007. Кроме того, 64-разрядные приложения SQL Server могут получать доступ к 32-разрядным файлам Jet и системы Office 2007, используя 32-разрядные службы SQL Server Integration Services (SSIS) в 64-разрядной среде Windows.

* **MSDADS**. С помощью поставщика Microsoft OLE DB Provider for Data Shaping (MSDADS) в приложении можно создавать иерархические связи между ключами, полями или наборами строк. С момента выпуска MDAC 2.1 в него не вносились существенные улучшения. Этот поставщик является нерекомендуемым. Корпорация Майкрософт рекомендует использовать XML вместо MSDADS.
* **Oracle ODBC and Oracle OLE DB**. Драйвер Microsoft Oracle ODBC (Oracle ODBC) и поставщик OLE DB для Oracle (Майкрософт) (Oracle OLE DB) предоставляют доступ к серверам базы данных Oracle. Они создаются с помощью интерфейса Oracle Call Interface (OCI) версии 7 и обеспечивают полную поддержку Oracle 7. Кроме того, он использует эмуляцию Oracle 7, чтобы предоставить ограниченную поддержку для баз данных Oracle 8. Oracle больше не поддерживает приложения, использующие OCI версии 7. Эти технологии являются нерекомендуемыми. При использовании источников данных Oracle следует перейти на предоставляемый Oracle драйвер и поставщик.
* **RDS**. Remote Data Services (RDS) — это собственный механизм Microsoft для доступа к удаленным объектам ADO Recordset через Интернет или интрасеть. Технология RDS является нерекомендуемой; существенные изменения в возможности RDS 2.1 не вносились. Корпорация Майкрософт выпустила .NET Framework, которая обладает широкими возможностями SOAP и заменяет компоненты RDS. После Windows 7 все серверные компоненты RDS будут удалены из операционной системы.
* **JRO**. Объекты репликации Jet (JRO) являются нерекомендуемыми. JRO используется в ADO с базами данных Jet ( *.mdb) для создания и сжатия баз данных Jet (.mdb) и выполнения Jet Replication Management. MDAC 2.7 будет последним выпуском. JRO не будет доступен в 64-разрядной операционной системе Windows. JRO не поддерживается в формате файлов Microsoft Access 2007 (* .accdb).
* **Поддержка 16-разрядных ODBC**. При использовании 16-разрядных приложений следует перейти на 32-разрядное приложение. 16-разрядные функции являются нерекомендуемыми и удаляются из 64-разрядных операционных систем. Дополнительные сведения см. в [статье базы знаний 896458](https://support.microsoft.com/kb/896458).
* **Простой поставщик OLEDB (MSDAOSP)** . Простой поставщик OLEDB предлагает платформу для быстрого создания поставщиков OLE DB с простыми данными. MSDAOSP является нерекомендуемым.
* **Библиотека курсоров ODBC**. Библиотека курсоров ODBC (ODBCCR32.dll) предоставляет ограниченные курсоры данных на стороне клиента. Библиотека курсоров ODBC является нерекомендуемой; в качестве замены приложение может использовать реализации курсоров на стороне сервера.
* **Удаленное взаимодействие OLE DB интерфейса вне процесса** Удаленное взаимодействие с интерфейсом OLEDB (msdaps.dll) — это попытка разрешить поставщикам OLE DB запуск вне процессов. Удаленное взаимодействие OLE DB интерфейса вне процесса не рекомендуется.
* **Сетевые библиотеки SQL AppleTalk и Banyan Vines**. Сетевые библиотеки SQL Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet и RPC являются нерекомендуемыми. Если вы используете любую из этих технологий, следует изменить приложения так, чтобы они использовали одну из других сетевых библиотек, например TCP/IP и именованный канал.

### <a name="mdacwdac-releases"></a>Выпуски MDAC/WDAC

Ниже приведен список сценариев поддержки для прошлых выпусков MDAC/WDAC, начиная с самого раннего.

* **MDAC 1.5, MDAC 2.0 и MDAC 2.1**. Эти версии MDAC были независимыми выпусками в составе пакета Windows NT Option Pack, пакета SDK для платформы Microsoft Windows или веб-узла MDAC. Эти версии MDAC больше не поддерживаются.
* **MDAC 2.5**. Эта версия MDAC входила в состав операционной системы Windows 2000. Пакеты обновления MDAC 2.5 входили в состав соответствующих пакетов обновлений для Windows 2000.
* **MDAC 2.6**. MDAC 2.6 RTM, SP1 и SP2 входили в состав Microsoft SQL Server 2000 RTM, SP1 и SP2, соответственно. Кроме того, эти пакеты обновления MDAC были выпущены на веб-узле MDAC в соответствии с графиком выпуска пакетов обновлений для Microsoft SQL Server 2000. Эту версию MDAC и ее пакеты обновления можно установить на платформах Windows 2000, Windows Millennium Edition, Windows NT, Windows 95 и Windows 98. Эта версия MDAC больше не поддерживается.
* **MDAC 2.7**. Эта версия MDAC входила в состав операционных систем Microsoft Windows XP RTM и SP1. Эту версию MDAC и ее пакеты обновления можно установить на платформах Windows 2000, Windows Millennium Edition, Windows NT и Windows 98. Эту версию можно установить на платформе Windows XP только с помощью операционной системы или ее пакетов обновлений. Эта версия MDAC больше не поддерживается.
* **MDAC 2.8**. Эта версия MDAC входила в состав Windows Server 2003 и Windows XP SP2 и более поздних версий. Вы также можете установить эту версию MDAC и ее пакеты обновления в Windows 2000.

  * 32-разрядная версия MDAC 2.8 также была выпущена на веб-узле MDAC одновременно с выпуском Windows Server 2003 для клиентов.
  * 64-разрядная версия MDAC 2.8 была выпущена с 64-разрядными версиями Windows Server 2003 и Windows XP.

* **Компоненты доступа к данным Windows DAC (WDAC)** . Название MDAC изменено на WDAC (компоненты доступа к данным Windows) начиная с Windows Vista и Windows Server 2008. WDAC входит в состав операционной системы и недоступен отдельно для повторного распространения. Обслуживание WDAC определяется жизненным циклом операционной системы.

  32-разрядная и 64-разрядная версии WDAC выпускаются с 32-разрядными и 64-разрядными версиями операционных систем Windows соответственно.

## <a name="obsolete-data-access-technologies"></a>Устаревшие технологии доступа к данным

Устаревшие технологии — это технологии, которые не были расширены или обновлены в нескольких выпусках продукта и будут исключены из будущих выпусков продукта. Не используйте эти технологии при написании новых приложений. При изменении существующих приложений, написанных с помощью этих технологий, рекомендуем перенести эти приложения на ADO.NET или другую текущую технологию.

Устаревшими считаются следующие компоненты:

* **DB-Library**. DB-Library — это модель программирования для SQL Server, которая содержит программный интерфейс C. С момента выхода SQL Server 6.5 в библиотеке DB-Library улучшения в возможности не вносились. Его последний выпуск — SQL Server 2000, и он не будет перенесен в 64-разрядную операционную систему Windows.
* **Embedded SQL (E-SQL)** . E-SQL — это модель программирования для SQL Server, которая позволяет внедрять инструкции Transact-SQL в код Visual C. Начиная с SQL Server 6.5, в E-SQL улучшения в возможности не вносились Его последний выпуск — SQL Server 2000, и он не будет перенесен в 64-разрядную операционную систему Windows.
* **Объекты доступа к данным (DAO)** . DAO предоставляет доступ к базам данных JET (Access). Этот программный интерфейс можно использовать в языках Microsoft Visual Basic, Microsoft Visual C++, а также в языках сценариев. Он входил в состав Microsoft Office 2000 и Office XP. DAO 3.6 — это последняя версия этой технологии. Она не будет доступна в 64-разрядной операционной системе Windows.
* **Remote Data Objects (RDO)** . RDO разрабатывалась специально для доступа к удаленным реляционным источникам данных ODBC и упрощает использование ODBC без сложного кода приложения. Она входила в состав Microsoft Visual Basic версий 4, 5 и 6. RDO версии 2.0 была последней версией этой технологии.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
