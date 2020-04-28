---
title: Подключение к SQL Serverу (MySQLToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0ec33e462f1b68d70a86a0fbf4f7cf0214d25770
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68103132"
---
# <a name="connecting-to-sql-server-mysqltosql"></a>Подключение к SQL Server (MySQLToSQL)
Чтобы перенести базы данных MySQL в SQL Server, необходимо подключиться к целевому экземпляру SQL Server. При подключении SSMA получает метаданные обо всех базах данных в экземпляре SQL Server и отображает метаданные базы данных в обозревателе метаданных SQL Server. SSMA хранит сведения об экземпляре SQL Server, к которому вы подключены, но не хранят пароли.  
  
Подключение к SQL Server остается активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к SQL Server, если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока вы не загрузит объекты базы данных в SQL Server и не перенесете данные.  
  
Метаданные экземпляра SQL Server не синхронизируются автоматически. Вместо этого для обновления метаданных в SQL Server обозревателе метаданных необходимо вручную обновить метаданные SQL Server. Дополнительные сведения см. в подразделе "синхронизация метаданных SQL Server" Далее в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Обязательные SQL Server разрешения  
Учетная запись, используемая для подключения к SQL Server, требует различных разрешений в зависимости от действий, выполняемых учетной записью.  
  
-   Чтобы преобразовать объекты MySQL в [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, обновить метаданные из SQL Server или сохранить преобразованный синтаксис в скрипты, учетная запись должна иметь разрешение на вход в экземпляр SQL Server.  
  
-   Чтобы загрузить объекты базы данных в SQL Server, минимальные требования к разрешениям являются членство в роли базы данных **db_owner** в целевой базе данных.  
  
## <a name="establishing-a-sql-server-connection"></a>Установка подключения SQL Server  
Прежде чем преобразовывать объекты базы данных MySQL в синтаксис SQL Server, необходимо установить соединение с экземпляром служб SQL Server, на котором необходимо перенести базу данных или базы MySQL.  
  
При определении свойств соединения также указывается база данных, в которую будут перенесены объекты и данные. Это сопоставление можно настроить на уровне схемы MySQL после подключения к SQL Server. Дополнительные сведения см. [в разделе Сопоставление баз данных MySQL с SQL Server схемами &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Прежде чем пытаться подключиться к SQL Server, убедитесь, что экземпляр SQL Server работает и может принимать подключения.  
  
**Подключение SQL Server**  
  
1.  В меню **файл** выберите команду **подключиться к SQL Server** (этот параметр включен после создания проекта).  
  
    Если ранее вы подключились к SQL Server, имя команды будет **повторно подключено к SQL Server**.  
  
2.  В диалоговом окне Соединение введите или выберите имя экземпляра SQL Server.  
  
    -   При подключении к экземпляру по умолчанию на локальном компьютере можно ввести **localhost** или точку (**.**).  
  
    -   При подключении к экземпляру по умолчанию на другом компьютере введите имя компьютера.  
  
    -   При подключении к именованному экземпляру на другом компьютере введите имя компьютера, затем обратную косую черту, а затем имя экземпляра, например Мисервер\минстанце..  
  
3.  Если экземпляр SQL Server настроен на прием подключений по нестандартному порту, введите номер порта, который используется для SQL Server соединений в поле **порт сервера** . Для экземпляра по умолчанию SQL Server номер порта по умолчанию — 1433. Для именованных экземпляров SSMA попытается получить номер порта из службы обозреватель SQL Server.  
  
4.  В поле **Проверка подлинности** выберите тип проверки подлинности, который будет использоваться для соединения. Чтобы использовать текущую учетную запись Windows, выберите **Проверка подлинности Windows**. Чтобы использовать SQL Server имя входа, выберите SQL Server проверка подлинности, а затем укажите имя входа и пароль.  
  
5.  Для безопасного подключения добавляются два элемента управления: флажки **Шифровать соединение** и **TrustServerCertificate** . Флажок **TrustServerCertificate** отображается только при установленном **шифровании соединения** . Если флажок **Шифровать соединение** установлен (true) и **TrustServerCertificate** не установлен (false), он будет проверять SQL Server SSL-сертификат. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы убедиться в этом, сертификат должен быть установлен на стороне клиента, а также на стороне сервера.  
  
6.  Нажмите кнопку "Подключить".  
  
**Совместимость более поздних версий**  
  
Ему разрешено подключаться и повторно подключаться к более поздним версиям SQL Server.  
  
1.  Вы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сможете подключиться к 2008 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если создан проект — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
2.  Вы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сможете подключиться к 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если проект создан в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, но ему не разрешено подключаться к более ранним версиям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например 2005.  
  
3.  Вы сможете [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключиться к 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если проект создан в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012.  
  
4.  Вы сможете подключиться только [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если создан проект — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014.  
  
5.  Совместимость более поздних версий недопустима для "SQL Azure".  
  
||||||||  
|-|-|-|-|-|-|-|  
|**Тип проекта и версия целевого сервера**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Версия: 9. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Версия: 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012<br />(Версия: 11. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014<br />(Версия: 12. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016<br />(Версия: 13. x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Да|Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016|||||Да||  
|SQL Azure||||||Да|  
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется в соответствии с типом проекта, но не в соответствии с версией, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с которой установлено соединение. В случае с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проектом 2005 преобразование выполняется в соответствии с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, даже если вы подключены к более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Метаданные SQL Server базы данных не обновляются автоматически. Метаданные в SQL Server обозревателе метаданных являются моментальным снимком метаданных при первом подключении к SQL Server или при последнем обновлении метаданных вручную. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объекта базы данных.  
  
**Синхронизация метаданных**  
  
1.  Убедитесь, что вы подключены к SQL Server.  
  
2.  В SQL Server обозревателе метаданных установите флажок рядом с базой данных или схемой базы данных, которую требуется обновить.  
  
    Например, чтобы обновить метаданные для всех баз данных, установите флажок рядом с пунктом databases (базы данных).  
  
3.  Щелкните правой кнопкой мыши базы данных или отдельную базу данных или схему базы данных, а затем выберите **синхронизировать с базой данных**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг миграции зависит от потребностей проекта:  
  
-   Сведения о настройке сопоставления между схемами MySQL и SQL Server базами данных и схемами см. в разделе [Сопоставление баз данных MySQL с SQL Server схемами &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Сведения о настройке параметров конфигурации для проектов см. в разделе [Установка параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Сведения о настройке сопоставления исходных и целевых типов данных см. в разделе [Сопоставление типов данных MySQL и SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Если не нужно выполнять какие – либо из этих задач, можно преобразовать определения объектов базы данных MySQL в определения объектов SQL Server. Дополнительные сведения см. в статье [Преобразование баз данных MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>См. также:  
[Перенос баз данных MySQL в SQL Server Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
