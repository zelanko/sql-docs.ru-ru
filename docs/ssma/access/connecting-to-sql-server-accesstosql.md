---
title: Подключение к SQL Serverу (Акцесстоскл) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006645"
---
# <a name="connecting-to-sql-server-accesstosql"></a>Подключение к SQL Server (Акцесстоскл)
Чтобы перенести базы данных Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в, необходимо подключиться к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При подключении SSMA получает метаданные о базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отображает метаданные базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозревателе метаданных. SSMA хранит сведения о том, к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] какому экземпляру вы подключены, но не хранят пароли.  
  
Подключение к SQL Server остается активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к SQL Server, если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока вы не загрузит объекты базы данных в SQL Server и не перенесете данные.  
  
Метаданные экземпляра SQL Server не синхронизируются автоматически. Вместо этого для обновления метаданных в SQL Server обозревателе метаданных необходимо вручную обновить метаданные SQL Server. Дополнительные сведения см. в подразделе "синхронизация метаданных SQL Server" Далее в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Обязательные SQL Server разрешения  
Для учетной записи, используемой для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключения к, требуются другие разрешения в зависимости от действий, выполняемых этой учетной записью.  
  
-   Чтобы преобразовать объекты доступа в [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, обновить метаданные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или сохранить преобразованный синтаксис в скрипты, учетная запись должна иметь разрешение на вход в экземпляр. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Чтобы загрузить объекты базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в и перенести их в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], минимальные требования к разрешениям являются членство в роли базы данных **db_owner** в целевой базе данных.  
  
## <a name="establishing-a-sql-server-connection"></a>Установка подключения SQL Server  
Перед преобразованием объектов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Access в синтаксис необходимо установить соединение с экземпляром, на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] котором необходимо перенести базы данных Access.  
  
При определении свойств соединения также указывается база данных, в которую будут перенесены объекты и данные. Это сопоставление можно настроить на уровне базы данных Access после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [сопоставление исходной и целевой баз данных](mapping-source-and-target-databases-accesstosql.md).  
  
> [!IMPORTANT]  
> Перед подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]убедитесь, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает и может принимать подключения. Дополнительные сведения см. в разделе «Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ядро СУБД» электронной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] документации по.  
  
**Подключение SQL Server**  
  
1.  В меню **файл** выберите **подключиться к SQL Server**.  
  
    Если ранее вы подключились к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имя команды будет **повторно подключено к SQL Server**.  
  
2.  В поле **имя сервера** введите или выберите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   При подключении к экземпляру по умолчанию на локальном компьютере можно ввести **localhost** или точку (**.**).  
  
    -   При подключении к экземпляру по умолчанию на другом компьютере введите имя компьютера.  
  
    -   При подключении к именованному экземпляру введите имя компьютера, обратную косую черту и имя экземпляра. Например: Мисервер\минстанце.  
  
    -   Чтобы подключиться к активному пользовательскому экземпляру [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], подключитесь с помощью протокола именованных каналов и укажите имя канала, \\ \\например .\pipe\sql\query.. Дополнительные сведения см. в документации по [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] .  
  
3.  Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для приема подключений по нестандартному порту, введите номер порта, используемый для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединений, в поле **порт сервера** . Для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]по умолчанию номер порта по умолчанию — 1433. Для именованных экземпляров SSMA попытается получить номер порта из службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузера.  
  
4.  В поле **база данных** введите имя целевой базы данных для переноса объектов и данных.  
  
    Этот параметр недоступен при повторном подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    Имя целевой базы данных не может содержать пробелы или специальные символы. Например, можно перенести базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных с именем "ABC". Но вы не можете перенести базы данных Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базу данных с именем a b-c.  
  
    Это сопоставление можно настроить для каждой базы данных после подключения. Дополнительные сведения см. в разделе [Сопоставление исходных и целевых баз данных](mapping-source-and-target-databases-accesstosql.md) .  
  
5.  В раскрывающемся меню **Проверка подлинности** выберите тип проверки подлинности, который будет использоваться для соединения. Чтобы использовать текущую учетную запись Windows, выберите **Проверка подлинности Windows**. Чтобы использовать имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, выберите **SQL Server проверка подлинности**, а затем укажите имя пользователя и пароль.  
  
6.  Для безопасного подключения добавляются два элемента управления: флажок **Шифровать соединение** и **TrustServerCertificate** . Флажок только при **шифровании подключения** установлен **TrustServerCertificate** . Если флажок **Шифровать соединение** установлен (true) и **TrustServerCertificate** не установлен (false), будет проверять SQL Server SSL-сертификат. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы убедиться в этом, сертификат должен быть установлен на стороне клиента, а также на стороне сервера.  
  
7.  Нажмите кнопку **Соединить**.  
  
**Совместимость более поздних версий**  
  
Ему разрешено подключаться и повторно подключаться к более поздним версиям SQL Server.  
  
1.  Вы сможете подключиться к SQL Server 2008 или SQL Server 2012, если проект создан SQL Server 2005.  
  
2.  Вы сможете подключиться к SQL Server 2012, когда создан проект SQL Server 2008, но не разрешается подключаться к более ранним версиям, т. е. SQL Server 2005.  
  
3.  Вы сможете подключиться только к SQL Server 2012, если проект создан SQL Server 2012.  
  
4.  Совместимость более поздних версий недействительна для SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**Тип проекта и версия целевого сервера**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 (версия: 9. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008 (версия: 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012 (версия: 11. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 (версия: 12. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016 (версия: 13. x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005|Да|Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008||Да|Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012|||Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016|||||Да||
|SQL Azure||||||Да|
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется в соответствии с типом проекта, но не в соответствии с версией SQL Server, к которой подключена. В случае проекта SQL Server 2005 преобразование выполняется по SQL Server 2005, даже если вы подключены к более поздней версии SQL Server (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы изменяются после подключения, можно синхронизировать метаданные с сервером.  
  
**Синхронизация метаданных SQL Server**  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозревателе метаданных щелкните правой кнопкой мыши **базы данных**и выберите **синхронизировать с базой данных**.  
  
## <a name="reconnecting-to-sql-server"></a>Повторное подключение к SQL Server  
Подключение будет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оставаться активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных не будут загружены в и не перенесены.  
  
Процедура повторного подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] совпадает с процедурой установки соединения.  
  
## <a name="next-steps"></a>Next Steps  
Если вы хотите настроить сопоставление между исходной и целевой базами данных, см. раздел [сопоставление исходной и целевой баз данных](mapping-source-and-target-databases-accesstosql.md) в противном случае следующим шагом является преобразование объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных в синтаксис с помощью инструкции [Convert Objects](converting-access-database-objects-accesstosql.md) .  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
