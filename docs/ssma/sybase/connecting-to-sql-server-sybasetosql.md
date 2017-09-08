---
title: "Подключение к SQL Server (SybaseToSQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- Connecting to SQL Server
ms.assetid: dd368a1a-45b0-40e9-b4d3-5cdb48c26606
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3dd8b595d897aad93d580447af4afed330cb71f9
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="connecting-to-sql-server-sybasetosql"></a>Подключение к SQL Server (SybaseToSQL)
Для переноса баз данных Sybase адаптивной Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], необходимо подключиться к любому из экземпляров целевого [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. При подключении SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и отображает метаданные базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных. SSMA хранит сведения о какой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] подключены, но не хранит пароли.  
  
Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] остается активным, пока закрыть проект. При повторном открытии проекта, необходимо повторно подключится [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Если требуется активное подключение к серверу. Можно работать вне сети до загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и переноса данных.  
  
Метаданные об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] автоматически не синхронизирована. Вместо этого, если вы хотите обновить метаданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных, необходимо вручную обновить [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных, как описано в «Synchronizing [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных» далее в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Разрешения требуется SQL Server  
Учетная запись, используемая для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] требуются различные разрешения в зависимости от действий, выполняемых этой учетной записи.  
  
-   Для преобразования объектов ASE для [!INCLUDE[tsql](../../includes/tsql_md.md)] синтаксис, чтобы обновить метаданные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], или чтобы сохранить преобразованный синтаксис скриптов, учетная запись должна иметь разрешение на вход экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Для загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], требование минимально необходимым разрешением является членство в **db_owner** роли базы данных в целевой базе данных.  
  
-   Для переноса данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], учетная запись должна быть членом **sysadmin** роли сервера. Это необходимо для запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] пакетов миграции данных агента.  
  
-   Для выполнения кода, который формируется SSMA учетная запись должна иметь **Execute** разрешения для всех определяемых пользователем функций в **ssma_syb** схему **sysdb** базы данных. Эти функции функциональность ASE системных функций и используемые преобразованные объекты.  
  
Если учетная запись, используемая для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для переноса всех задач, учетная запись должна быть членом **sysadmin** роли сервера.  
  
## <a name="establishing-a-sql-server-connection"></a>Установление соединения с SQL Server  
Перед началом преобразования ASE объекты базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксис, необходимо установить соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] которой вы хотите перенести ASE базы данных или базы данных.  
  
При определении свойств соединения, можно также указать базы данных, где будет выполнена миграция объектов и данных. Это сопоставление на уровне схемы ASE можно настроить после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения см. в разделе [сопоставление схем Sybase ASE для схемы SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
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
  
    Этот параметр недоступен, если повторное подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
5.  В **проверки подлинности** выберите тип проверки подлинности, используемый для соединения. Чтобы использовать текущую учетную запись Windows, выберите **проверки подлинности Windows**. Для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] входа в систему, выберите **проверки подлинности SQL Server** и укажите имя входа и пароль.  
  
6.  Для безопасного подключения добавляются два элемента управления, **шифровать соединение** и **TrustServerCertificate** флажки. Только если **шифровать соединение** установлен, **TrustServerCertificate** флажок становится видимым. Когда **шифровать соединение** проверяется (true) и **TrustServerCertificate** снят (false), он будет проверки SQL Server SSL-сертификата. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы обеспечить это, необходимо установить сертификат на стороне клиента, так и на стороне сервера.  
  
7.  Нажмите кнопку **Соединить**.  
  
**Выше версии совместимости**  
  
-   Можно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 при миграции проект, созданный [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   Можно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 при миграции проект, созданный [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, но вы не сможете подключиться к более ранние версии, т. е. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   Можно подключиться только к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 при проект, созданный в SQL Server 2012.  
  
-   Выше совместимость версий не является допустимым для SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**ВЕРСИЯ проекта ТИПА Vs целевого сервера**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005<br /> (Версия: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008<br /> (Версия: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 <br />(Version:13.x)|SQL Azure|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|Да|Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||Да|Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014||||Да|Да|| 
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016|||||Да||  
|SQL Azure||||||Да|  
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется согласно типа проекта, но не согласно версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] вы подключены. В случае возникновения [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проекта 2005 преобразование выполняется согласно [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] даже если вы подключены к более новой версии 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016)  
  
## <a name="reconnecting-to-sql-server"></a>Повторное подключение к SQL Server  
Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] остается активным, пока закрыть проект. При повторном открытии проекта, необходимо повторно подключится [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Если требуется активное подключение к серверу. Можно работать вне сети до обновления метаданных, загрузка объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], и перенести данные.  
  
Процедуры для повторного подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] является так же, как для установления подключения.  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Метаданные о [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных не обновляется автоматически. Метаданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных представляет собой моментальный снимок метаданные при первом подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], или последнего времени, когда вручную обновленных метаданных. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объекта базы данных.  
  
**Для синхронизации метаданных**  
  
1.  Убедитесь, что вы подключены к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
2.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных, установите флажок напротив базы данных или схемы, которую необходимо обновить базы данных.  
  
    Например, чтобы обновить метаданные для всех баз данных, установите в поле **баз данных**.  
  
3.  Щелкните правой кнопкой мыши баз данных или отдельной базы данных или схемы базы данных, а затем выберите **синхронизации с базой данных**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе переноса, зависит от требований проекта:  
  
-   Если вы хотите настроить сопоставление между ASE базы данных и схемы и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных и схемы, в разделе [Sybase ASE схемы сопоставления схемы SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
-   Если вы хотите настроить параметры конфигурации для проектов, см. раздел [задание параметров проекта &#40; SybaseToSQL &#41; ](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
-   Если требуется пользовательское сопоставление исходных и целевых типов данных, см. раздел [сопоставления Sybase ASE и типов данных SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   Если не нужно выполнять какие-либо из них, можно преобразовать определения объектов базы данных Sybase ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] определений объекта. Дополнительные сведения см. в разделе [преобразование объектов базы данных Sybase ASE &#40; SybaseToSQL &#41; ](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Sybase ASE в SQL Server — база данных Azure SQL &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

