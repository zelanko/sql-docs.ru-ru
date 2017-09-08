---
title: "Подключение к SQL Server (DB2eToSQL) | Документы Microsoft"
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
ms.assetid: b59803cb-3cc6-41cc-8553-faf90851410e
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4fbfc112af0d0fb2b9bc62cdf0c3af4803fe731f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="connecting-to-sql-server-db2etosql"></a>Подключение к SQL Server (DB2eToSQL)
Для переноса баз данных DB2 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 г. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]БД SQL 2014 или Azure, необходимо подключиться к одному из этих экземпляров целевого [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. При подключении SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и отображает метаданные базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных. SSMA хранит сведения о какой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] подключены, но не хранит пароли.  
  
Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] остается активным, пока закрыть проект. При повторном открытии проекта, необходимо повторно подключится [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Если требуется активное подключение к серверу. Можно работать вне сети до загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и переноса данных.  
  
Метаданные об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] автоматически не синхронизирована. Вместо этого для обновления метаданных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных, необходимо вручную обновить [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных. Дополнительные сведения см. в разделе «синхронизация [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных» далее в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Разрешения требуется SQL Server  
Учетная запись, используемая для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] требуются различные разрешения в зависимости от действий, выполняемых в учетной записи:  
  
-   Для преобразования объектов DB2 для [!INCLUDE[tsql](../../includes/tsql_md.md)] синтаксис, чтобы обновить метаданные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], или чтобы сохранить преобразованный синтаксис скриптов, учетная запись должна иметь разрешение на вход в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Для загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], учетная запись должна быть членом **sysadmin** роли сервера. Это необходимо для установки сборки среды CLR.  
  
-   Для переноса данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], учетная запись должна быть членом **sysadmin** роли сервера. Это необходимо для запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] пакетов миграции данных агента.  
  
-   Для выполнения кода, который формируется SSMA учетная запись должна иметь **Execute** разрешения для всех определяемых пользователем функций в **ssma_DB2** схемы целевой базы данных. Эти функции функциональность DB2 системных функций и используемые преобразованные объекты.  
  
Если учетная запись, используемая для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для переноса всех задач, учетная запись должна быть членом **sysadmin** роли сервера.  
  
## <a name="establishing-a-sql-server-connection"></a>Установление соединения с SQL Server  
Перед началом преобразования объектов базы данных DB2 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксис, необходимо установить соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] место для переноса баз данных или базы данных DB2.  
  
При определении свойств соединения, можно также указать базы данных, где будет выполнена миграция объектов и данных. Это сопоставление на уровне схемы DB2 можно настроить после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения см. в разделе [сопоставление схем DB2 для схемы SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
> [!IMPORTANT]  
> Прежде чем пытаться подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], убедитесь, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] запущена и может принимать подключения.  
  
**Для подключения к SQL Server**  
  
1.  На **файл** последовательно выберите пункты **подключение к SQL Server**.  
  
    Если ранее подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], будет иметь имя команды **повторно подключиться к SQL Server**.  
  
2.  В диалоговом окне соединения, введите или выберите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   При подключении к экземпляру по умолчанию на локальном компьютере, можно ввести **localhost** или точку (**.**).  
  
    -   При подключении к экземпляру по умолчанию на другом компьютере, введите имя компьютера.  
  
    -   Если вы подключаетесь к именованному экземпляру на другом компьютере, введите имя компьютера, следуют обратную косую черту и имя экземпляра, например Сервер\экземпляр.  
  
3.  Если ваш экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] настроен на прием подключений через порт не по умолчанию, введите номер порта, используемый для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] подключения в **порт сервера** поле. Для экземпляра по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], по умолчанию используется порт 1433. Для именованных экземпляров SSMA будет пытаться получить номер порта от [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] служба браузера.  
  
4.  В **базы данных** введите имя целевой базы данных.  
  
    Этот параметр недоступен при повторном подключении [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
5.  В **проверки подлинности** выберите тип проверки подлинности, используемый для соединения. Чтобы использовать текущую учетную запись Windows, выберите **проверки подлинности Windows**. Для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] входа в систему, выберите **проверки подлинности SQL Server**, а затем укажите имя входа и пароль.  
  
6.  Для безопасного подключения добавляются два элемента управления, **шифровать соединение** и **TrustServerCertificate** флажки. Только если **шифровать соединение** установлен, **TrustServerCertificate** флажок становится видимым. Когда **шифровать соединение** проверяется (true) и **TrustServerCertificate** снят (false), он будет проверки SQL Server SSL-сертификата. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы обеспечить это, необходимо установить сертификат на стороне клиента, так и на стороне сервера.  
  
7.  Нажмите кнопку **Соединить**.  
  
**Выше версии совместимости**  
  
-   Можно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 при миграции проект, созданный [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   Можно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 при миграции проект, созданный [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, но вы не сможете подключиться к более ранние версии, т. е. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   Можно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 при проект, созданный в SQL Server 2012.  
  
||||||  
|-|-|-|-|-|  
|**ВЕРСИЯ проекта ТИПА Vs целевого сервера**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 <br />(Version:13.x)|База данных Azure SQL|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014||Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014|||Да||  
|База данных Azure SQL||||Да|  
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется согласно типа проекта, но не согласно версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] вы подключены. В случае возникновения [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 г. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных SQL Server 2016 или Azure.  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Метаданные о [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных не обновляется автоматически. Метаданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных представляет собой моментальный снимок метаданные при первом подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], или последнего времени, когда вручную обновленных метаданных. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объекта базы данных.  
  
**Для синхронизации метаданных**  
  
1.  Убедитесь, что вы подключены к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
2.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных, установите флажок напротив базы данных или схемы, которую необходимо обновить базы данных.  
  
    Например, чтобы обновить метаданные для всех баз данных, установите в поле **баз данных**.  
  
3.  Щелкните правой кнопкой мыши **баз данных**, или отдельной базы данных или схемы базы данных, а затем выберите **синхронизации с базой данных**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе переноса, зависит от требований проекта:  
  
-   Настройка сопоставления между схемами DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных и схемы, в разделе [схемы DB2 сопоставления схемы SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
-   Чтобы настроить параметры конфигурации для проектов, в разделе [параметры проекта &#40; Преобразование &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md) и связанных разделах.  
  
-   Настройка сопоставления исходных и целевых типов данных, в разделе [сопоставления DB2 и типов данных SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   Если необходимо выполнить эти действия, вы можете преобразовать определения объектов базы данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] определений объекта. Дополнительные сведения см. в разделе [преобразование схемы DB2 &#40; DB2ToSQL &#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных DB2 в SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  

