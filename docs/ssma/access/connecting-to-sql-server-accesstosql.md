---
title: "Подключение к SQL Server (AccessToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
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
caps.latest.revision: 24
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e9f2633151345d57fbba2fe7c40b3ca52b492e68
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="connecting-to-sql-server-accesstosql"></a>Подключение к SQL Server (AccessToSQL)
Для переноса базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], необходимо подключиться к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. При подключении SSMA получает метаданные о базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и отображает метаданные базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных. SSMA хранит сведения о какой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] подключены, но не хранит пароли.  
  
Подключение к SQL Server остается активным, если закрыть проект. При повторном открытии проекта, необходимо повторно подключить к серверу SQL Server, если требуется активное подключение к серверу. Вы можете работать вне сети до загрузки объектов базы данных в SQL Server и перенос данных.  
  
Метаданные экземпляра SQL Server автоматически не синхронизированы. Вместо этого для обновления метаданных в обозревателе метаданных SQL Server, необходимо вручную обновить метаданные SQL Server. Дополнительные сведения см. в разделе «Синхронизация метаданные SQL Server» далее в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Разрешения требуется SQL Server  
Учетная запись, используемая для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] требуются различные разрешения в зависимости от действий, выполняемых этой учетной записи.  
  
-   Для преобразования объектов доступа к [!INCLUDE[tsql](../../includes/tsql_md.md)] синтаксис для обновление метаданных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], или чтобы сохранить преобразованный синтаксис скриптов, учетная запись должна иметь разрешение на вход экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Для загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], требование минимально необходимым разрешением является членство в **db_owner** роли базы данных в целевой базе данных.  
  
## <a name="establishing-a-sql-server-connection"></a>Установление соединения с SQL Server  
Перед началом преобразования объектов базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксис, необходимо установить соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] место для переноса базы данных Access.  
  
При определении свойств соединения, можно также указать базы данных, где будет выполнена миграция объектов и данных. Это сопоставление на уровне базы данных Access можно настроить после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения см. в разделе [сопоставление исходной и целевой баз данных](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
> [!IMPORTANT]  
> Перед подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], убедитесь, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] запущена и может принимать подключения. Дополнительные сведения см. в разделе «подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] компонент Database Engine» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
**Для подключения к SQL Server**  
  
1.  На **файл** последовательно выберите пункты **подключение к SQL Server**.  
  
    Если ранее подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], будет иметь имя команды **повторно подключиться к SQL Server**.  
  
2.  В **имя сервера** введите или выберите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   При подключении к экземпляру по умолчанию на локальном компьютере, можно ввести **localhost** или точку (**.**).  
  
    -   При подключении к экземпляру по умолчанию на другом компьютере, введите имя компьютера.  
  
    -   При подключении к именованному экземпляру введите имя компьютера, обратную косую черту и имя экземпляра. Например: Сервер\экземпляр.  
  
    -   Для подключения к активному экземпляру пользователя [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], подключение по именованным каналам протокола и указав имя канала, такие как \\ \\.\pipe\sql\query. Дополнительные сведения см. в разделе [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] документации.  
  
3.  Если ваш экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] настроен на прием подключений через порт не по умолчанию, введите номер порта, используемый для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] подключения в **порт сервера** поле. Для экземпляра по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], по умолчанию используется порт 1433. Для именованных экземпляров SSMA будет пытаться получить номер порта от [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] служба браузера.  
  
4.  В **базы данных** введите имя целевой базы данных для миграции данных и объектов.  
  
    Этот параметр недоступен, если повторное подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    Имя целевой базы данных не может содержать пробелы или специальные символы. Например, можно перенести базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с именем «abc». Но не может переносить базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с именем «b-c».  
  
    Это сопоставление каждой базы данных можно настроить, после подключения. Дополнительные сведения см. в разделе [сопоставление исходной и целевой баз данных](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
5.  В **проверки подлинности** раскрывающееся меню, выберите тип проверки подлинности, используемый для соединения. Чтобы использовать текущую учетную запись Windows, выберите **проверки подлинности Windows**. Для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] входа в систему, выберите **проверки подлинности SQL Server**, а затем укажите имя пользователя и пароль.  
  
6.  Для безопасного подключения добавляются два элемента управления, **шифровать соединение** флажок и **TrustServerCertificate** флажок. Только если **шифровать соединение** флажок **TrustServerCertificate** отображается флажок. Когда **шифровать соединение** — checked(true) и **TrustServerCertificate** является unchecked(false), будет выполнять проверку сертификата SQL Server SSL. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы обеспечить это, необходимо установить сертификат на стороне клиента, так и на стороне сервера.  
  
7.  Нажмите кнопку **Соединить**.  
  
**Выше совместимость версий**  
  
Он может подключаться или повторно подключиться к более поздним версиям SQL Server.  
  
1.  Можно подключиться к SQL Server 2008 или SQL Server 2012, когда проект, созданный в SQL Server 2005.  
  
2.  Можно подключиться к SQL Server 2012, если проект, созданный в SQL Server 2008, но не может подключиться к более ранние версии, т. е. SQL Server 2005.  
  
3.  Можно подключиться только SQL Server 2012, когда проект, созданный в SQL Server 2012.  
  
4.  Выше совместимость версий не является допустимым для SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**ВЕРСИЯ проекта ТИПА Vs целевого сервера**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2005 г. (версия: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2008 (версия: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 (Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 (Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2016 (Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|Да|Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||Да|Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014||||Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016|||||Да||
|SQL Azure||||||Да|
  
> [!IMPORTANT]  
> Согласно типа проекта, но не согласно версии SQL Server, подключение выполняется преобразование объектов базы данных. В случае проекта SQL Server 2005 преобразование выполняется в соответствии с SQL Server 2005 несмотря на то, что вы подключены к более новой версии SQL Server (SQL Server 2008 и SQL Server 2012 или SQL Server 2014 или SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] изменения схемы после подключения, вы можете синхронизировать метаданные с сервера.  
  
**Для синхронизации метаданных SQL Server**  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных, щелкните правой кнопкой мыши **баз данных**, а затем выберите **синхронизации с базой данных**.  
  
## <a name="reconnecting-to-sql-server"></a>Повторное подключение к SQL Server  
Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] остается активным, пока закрыть проект. При повторном открытии проекта, необходимо повторно подключится [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Если требуется активное подключение к серверу. Можно работать вне сети до загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и переноса данных.  
  
Процедуры для повторного подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] является так же, как для установления подключения.  
  
## <a name="next-steps"></a>Следующие шаги  
Если вы хотите настроить сопоставление между исходной и целевой баз данных, см. раздел [сопоставления источника и целевым базам данных](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4) в противном случае следующим шагом является преобразование объектов базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с помощью синтаксиса [преобразования объектов базы данных](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  

