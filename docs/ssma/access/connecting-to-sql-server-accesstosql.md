---
title: Подключение к SQL Server (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- authentication
- instance of SQL Server
- metadata, refreshing
- ports
- refreshing metadata
- spaces in database names
- special characters
- SQL Server
- SQL Server, connecting
- SQL Server, connecting to
- SQL Server, reconnecting
ms.assetid: f84cf007-ddf1-4396-a07c-3e0729abc769
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 4630ae8d92dbf0e9b1c5bf615dd82d436a5751f5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006645"
---
# <a name="connecting-to-sql-server-accesstosql"></a>Подключение к SQL Server (AccessToSQL)
Для переноса баз данных Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо подключиться к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При подключении, SSMA получает метаданные о базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отображает метаданные базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных. SSMA хранит сведения о какой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключены, но не хранит пароли.  
  
Подключение к SQL Server остается активным, пока не закрыть проект. При повторном открытии проекта, вы должны повторно подключиться к SQL Server если требуется активное подключение к серверу. Вы можете работать вне сети до загрузки объектов базы данных в SQL Server и перенос данных.  
  
Метаданные об экземпляре SQL Server автоматически не синхронизирован. Вместо этого для обновления метаданных в обозревателе метаданных SQL Server, необходимо вручную обновить метаданные SQL Server. Дополнительные сведения см. в разделе «Синхронизация метаданных SQL Server» далее в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Разрешения требуется SQL Server  
Учетная запись, которая используется для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требует разных разрешений в зависимости от действия, выполняемые с этой учетной записи.  
  
-   Для преобразования объектов доступа к [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, чтобы обновить метаданные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или чтобы сохранить преобразованный синтаксис скриптов, она должна иметь разрешение на вход в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Для загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], требование минимально необходимым разрешением является членство в **db_owner** роли базы данных в целевую базу данных.  
  
## <a name="establishing-a-sql-server-connection"></a>Установки подключения к серверу SQL  
Перед началом преобразования объектов базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис, необходимо установить подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] которых необходимо выполнить миграцию баз данных Access.  
  
При определении свойств соединения, также указать базу данных, где объекты и данные будут перенесены. Это сопоставление на уровне базы данных Access можно настроить, после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [сопоставление исходной и целевой баз данных](mapping-source-and-target-databases-accesstosql.md).  
  
> [!IMPORTANT]  
> Перед подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], убедитесь, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает и может принимать подключения. Дополнительные сведения см. в разделе «подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонент Database Engine» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
**Для подключения к SQL Server**  
  
1.  На **файл** меню, выберите **подключение к SQL Server**.  
  
    Если вы ранее подключались к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], команда будет называться **повторно подключиться к SQL Server**.  
  
2.  В **имя_сервера** введите или выберите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Если вы подключаетесь к экземпляру по умолчанию на локальном компьютере, можно ввести **localhost** или точку ( **.** ).  
  
    -   Если вы подключаетесь к экземпляру по умолчанию на другом компьютере, введите имя компьютера.  
  
    -   Если вы подключаетесь к именованному экземпляру, введите имя компьютера, обратную косую черту и имя экземпляра. Пример: Сервер\экземпляр.  
  
    -   Для подключения к активному экземпляру пользователя из [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], подключение по именованным каналам протокола и указав имя канала, такие как \\ \\.\pipe\sql\query. Дополнительные сведения см. в разделе [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] документации.  
  
3.  Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен на прием подключений через нестандартный порт, введите номер порта, который используется для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключений в **порт сервера** поле. Для экземпляра по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], номер порта по умолчанию — 1433. Для именованных экземпляров SSMA будет пытаться получить номер порта из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы браузера.  
  
4.  В **базы данных** введите имя целевой базы данных для миграции данных и объектов.  
  
    Этот параметр недоступен при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    Имя целевой базы данных не может содержать пробелы или специальные символы. Например, можно перенести базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных с именем «abc». Но нельзя выполнить миграцию баз данных Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных с именем «b-c».  
  
    Это сопоставление каждой базы данных можно настроить, после подключения. Дополнительные сведения см. в разделе [сопоставление исходной и целевой баз данных](mapping-source-and-target-databases-accesstosql.md)  
  
5.  В **проверки подлинности** раскрывающееся меню, выберите тип проверки подлинности, используемый для соединения. Чтобы использовать текущую учетную запись Windows, выберите **проверки подлинности Windows**. Для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа, выберите **проверки подлинности SQL Server**, а затем укажите имя пользователя и пароль.  
  
6.  Для безопасного подключения, добавляются два элемента управления, **шифровать соединение** флажок и **TrustServerCertificate** флажок. Только тогда, когда **шифровать соединение** флажок **TrustServerCertificate** отображается флажок. Когда **шифровать соединение** — checked(true) и **TrustServerCertificate** является unchecked(false), будет выполнять проверку сертификата SQL Server SSL. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы обеспечить это, необходимо установить сертификат на стороне клиента, а также на стороне сервера.  
  
7.  Нажмите кнопку **Соединить**.  
  
**Выше совместимость версий**  
  
Он может подключаться или повторно подключиться к более поздним версиям SQL Server.  
  
1.  Можно подключиться к SQL Server 2008 или SQL Server 2012, когда проект, созданный в SQL Server 2005.  
  
2.  Можно подключиться к SQL Server 2012, если проект, созданный настроен SQL Server 2008, но он не разрешено подключаться к более ранние версии, т. е. SQL Server 2005.  
  
3.  Можно подключиться к только SQL Server 2012, когда проект, созданный в SQL Server 2012.  
  
4.  Выше совместимость версий не является допустимым для SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**ВЕРСИЯ целевого сервера Vs тип проекта**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 (версия: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 (версия: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 (Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 (Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 (Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Да|Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Да|Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||||Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Да||
|SQL Azure||||||Да|
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется в соответствии с типом проекта, но не в соответствии с версии SQL Server, подключенных к. В случае проекта SQL Server 2005 преобразование выполняется в соответствии с SQL Server 2005 несмотря на то, что вы подключены к более поздней версии SQL Server (SQL Server 2008 или SQL Server 2012 или SQL Server 2014 или SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы изменяют после подключения, вы можете синхронизировать метаданные с сервера.  
  
**Для синхронизации метаданных SQL Server**  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, щелкните правой кнопкой мыши **баз данных**, а затем выберите **синхронизация с базой данных**.  
  
## <a name="reconnecting-to-sql-server"></a>Повторное подключение к SQL Server  
Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остается активным, пока не закрыть проект. При повторном открытии проекта, необходимо повторно подключить к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если требуется активное подключение к серверу. Автономном время загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и перенос данных.  
  
Процедура при повторном подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] совпадает со значением процедуры для установления соединения.  
  
## <a name="next-steps"></a>Следующие шаги  
Если вы хотите настроить сопоставление между исходной и целевой баз данных, см. в разделе [сопоставление исходной и целевой баз данных](mapping-source-and-target-databases-accesstosql.md) в противном случае следующим шагом является преобразование объектов базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью синтаксиса [преобразования объекты базы данных](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
