---
title: Подключение к SQL Server (MySQLToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9f3b5b835f6fa5db7f88accacf041b8079ca954b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-sql-server-mysqltosql"></a>Подключение к SQL Server (MySQLToSQL)
Для переноса баз данных MySQL в SQL Server, необходимо подключиться к целевому экземпляру SQL Server. При подключении SSMA получает метаданные обо всех базах данных в экземпляре SQL Server и отображает метаданные базы данных в обозревателе метаданных SQL Server. SSMA хранит сведения о экземпляра SQL Server, вы подключены, но не хранит пароли.  
  
Подключение к SQL Server остается активным, если закрыть проект. При повторном открытии проекта, необходимо повторно подключить к серверу SQL Server, если требуется активное подключение к серверу. Вы можете работать вне сети до загрузки объектов базы данных в SQL Server и перенос данных.  
  
Метаданные экземпляра SQL Server автоматически не синхронизированы. Вместо этого для обновления метаданных в обозревателе метаданных SQL Server, необходимо вручную обновить метаданные SQL Server. Дополнительные сведения см. в разделе «Синхронизация метаданные SQL Server» далее в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Разрешения требуется SQL Server  
Учетная запись, используемая для подключения к SQL Server требуются различные разрешения в зависимости от действий, выполняемых в учетной записи:  
  
-   Для преобразования объектов MySQL для [!INCLUDE[tsql](../../includes/tsql_md.md)] синтаксис, чтобы обновить метаданные из SQL Server или сохранить преобразованный синтаксис для сценариев, учетная запись должна иметь разрешение на вход в экземпляр SQL Server.  
  
-   Для загрузки объектов базы данных в SQL Server, требование минимально необходимым разрешением является членство в **db_owner** роли базы данных в целевой базе данных.  
  
## <a name="establishing-a-sql-server-connection"></a>Установление соединения с SQL Server  
Перед началом преобразования объектов базы данных MySQL в синтаксис SQL Server, необходимо установить подключение к экземпляру SQL Server, где требуется выполнить миграцию базы данных MySQL или баз данных.  
  
При определении свойств соединения, можно также указать базы данных, где будет выполнена миграция объектов и данных. Это сопоставление на уровне схемы MySQL можно настроить, после подключения к SQL Server. Дополнительные сведения см. в разделе [сопоставления баз данных MySQL в схемы SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Прежде чем пытаться подключиться к SQL Server, убедитесь, что экземпляр SQL Server запущен и может принимать подключения.  
  
**Для подключения к SQL Server**  
  
1.  На **файл** последовательно выберите пункты **подключение к SQL Server** (этот параметр включен после создания проекта).  
  
    Если ранее вы подключились к SQL Server, имя команды будет **повторно подключиться к SQL Server**.  
  
2.  В диалоговом окне соединения введите или выберите имя экземпляра SQL Server.  
  
    -   При подключении к экземпляру по умолчанию на локальном компьютере, можно ввести **localhost** или точку (**.**).  
  
    -   При подключении к экземпляру по умолчанию на другом компьютере, введите имя компьютера.  
  
    -   Если вы подключаетесь к именованному экземпляру на другом компьютере, введите имя компьютера, следуют обратную косую черту и имя экземпляра, например Сервер\экземпляр.  
  
3.  Если экземпляр SQL Server настроен на прием подключений через порт не по умолчанию, введите номер порта, используемый для подключения к серверу SQL в **порт сервера** поле. Для экземпляра по умолчанию SQL Server, по умолчанию используется порт 1433. Для именованных экземпляров SSMA будет пытаться получить номер порта от службы обозревателя SQL Server.  
  
4.  В **проверки подлинности** выберите тип проверки подлинности, используемый для соединения. Чтобы использовать текущую учетную запись Windows, выберите **проверки подлинности Windows**. Чтобы использовать имя входа SQL Server, выберите проверку подлинности SQL Server и укажите имя входа и пароль.  
  
5.  Для безопасного подключения добавляются два элемента управления, **шифровать соединение** и **TrustServerCertificate** флажки. Только если **шифровать соединение** установлен, **TrustServerCertificate** флажок становится видимым. Когда **шифровать соединение** проверяется (true) и **TrustServerCertificate** снят (false), он будет проверки SQL Server SSL-сертификата. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы обеспечить это, необходимо установить сертификат на стороне клиента, так и на стороне сервера.  
  
6.  Щелкните "Подключить".  
  
**Выше совместимость версий**  
  
Он может подключаться или повторно подключиться к более поздним версиям SQL Server.  
  
1.  Можно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 проект, созданный при [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
2.  Можно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 проект, созданный при [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, но не может подключиться к более ранние версии, т. е. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
3.  Можно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 проект, созданный при [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012.  
  
4.  Можно подключиться только к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 проект, созданный при [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 г.  
  
5.  Выше совместимость версий не является допустимым для «SQL Azure».  
  
||||||||  
|-|-|-|-|-|-|-|  
|**ВЕРСИЯ проекта ТИПА Vs целевого сервера**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005<br /> (Версия: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008<br /> (Версия: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012<br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014<br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016<br />(Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|Да|Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014||||Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2016|||||Да||  
|SQL Azure||||||Да|  
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется согласно типа проекта, но не согласно версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] подключен. В случае возникновения [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проекта 2005 преобразование выполняется согласно [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] даже если вы подключены к более новой версии 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] (SQL Server 2008 и SQL Server 2012 или SQL Server 2014 или SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Метаданные базы данных SQL Server не обновляется автоматически. Метаданные в обозревателе метаданных SQL Server, моментальный снимок метаданные при при первом подключении к SQL Server или последнего времени, когда вручную обновленных метаданных. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объекта базы данных.  
  
**Для синхронизации метаданных**  
  
1.  Убедитесь, что вы подключены к серверу SQL Server.  
  
2.  В обозревателе метаданных SQL Server установите флажок рядом с именем базы данных или схемы базы данных, которую необходимо обновить.  
  
    Например для обновления метаданных для всех баз данных, выберите флажок рядом с базами данных.  
  
3.  Щелкните правой кнопкой мыши баз данных, или отдельной базы данных или схемы базы данных, а затем выберите **синхронизации с базой данных**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе переноса, зависит от требований проекта:  
  
-   Настройка сопоставления между схемами и баз данных SQL Server и MySQL схемы, в разделе [сопоставления баз данных MySQL в схемы SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Чтобы настроить параметры конфигурации для проектов, в разделе [задание параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Настройка сопоставления исходных и целевых типов данных, в разделе [MySQL сопоставления и типов данных SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Если необходимо выполнить эти действия, можно преобразовать определения объектов базы данных MySQL в определения объектов SQL Server. Дополнительные сведения см. в разделе [преобразование баз данных MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>См. также  
[Миграция MySQL баз данных SQL Server — Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
