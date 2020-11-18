---
title: Подключение к SQL Serverу (Акцесстоскл) | Документация Майкрософт
description: Узнайте, как подключиться к целевому экземпляру базы данных SQL для миграции баз данных Access. SSMA получает метаданные о базах данных в базе данных SQL.
ms.prod: sql
ms.custom: ''
ms.date: 11/16/2020
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 1bd54d3fdf90447dbbf8b35a96c6b454ca6c4e56
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94869570"
---
# <a name="connecting-to-sql-server-accesstosql"></a>Подключение к SQL Server (Акцесстоскл)

Чтобы перенести базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо подключиться к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При подключении SSMA получает метаданные о базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отображает метаданные базы данных в **SQL Server обозревателе метаданных**. SSMA хранит сведения о том, к какому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вы подключены, но не хранят пароли.

Подключение будет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оставаться активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока объекты базы данных не будут загружены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не перенесены.

Метаданные экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не синхронизируются автоматически. Вместо этого для обновления метаданных в SQL Server обозревателе метаданных необходимо вручную обновить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданные. Дополнительные сведения см. в подразделе "синхронизация метаданных SQL Server" Далее в этом разделе.

## <a name="required-sql-server-permissions"></a>Обязательные SQL Server разрешения

Для учетной записи, используемой для подключения к, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуются другие разрешения в зависимости от действий, выполняемых учетной записью.

- Чтобы преобразовать объекты доступа в [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, обновить метаданные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или сохранить преобразованный синтаксис в скрипты, учетная запись должна иметь разрешение на вход в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

- Чтобы загрузить объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , учетная запись должна быть членом роли базы данных **db_ddladmin** .

- Чтобы перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , учетная запись должна быть членом роли базы данных **db_owner** .

## <a name="establishing-a-sql-server-connection"></a>Установка подключения SQL Server

Перед преобразованием объектов базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис необходимо установить соединение с экземпляром, на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] котором необходимо перенести базы данных Access.

При определении свойств соединения также указывается база данных, в которую будут перенесены объекты и данные. Это сопоставление можно настроить на уровне базы данных Access после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [сопоставление исходной и целевой баз данных](mapping-source-and-target-databases-accesstosql.md).

> [!IMPORTANT]
> Перед подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Убедитесь, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает и может принимать подключения.

Подключение к диспетчеру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:

1. В меню **файл** выберите **подключиться к SQL Server**.
   Если ранее вы подключились к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , имя команды будет **повторно подключено к SQL Server**.

2. В поле **имя сервера** введите или выберите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
   - При подключении к экземпляру по умолчанию на локальном компьютере можно ввести `localhost` или точку ( `.` ).
   - При подключении к экземпляру по умолчанию на другом компьютере введите имя компьютера.
   - При подключении к именованному экземпляру введите имя компьютера, обратную косую черту и имя экземпляра. Например, так: `MyServer\MyInstance`.
   - Чтобы подключиться к активному пользовательскому экземпляру [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] , подключитесь с помощью протокола именованных каналов и укажите имя канала, например `\\.\pipe\sql\query` . Дополнительные сведения см. в документации по [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)].

3. Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для приема подключений по нестандартному порту, введите номер порта, используемый для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединений, в поле **порт сервера** . Для экземпляра по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] номер порта по умолчанию — 1433. Для именованных экземпляров SSMA попытается получить номер порта из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы браузера.

4. В поле **база данных** введите имя целевой базы данных для переноса объектов и данных.
   Этот параметр недоступен при повторном подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
   Имя целевой базы данных не может содержать пробелы или специальные символы. Например, можно перенести базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных с именем `abc` . Но нельзя перенести базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных с именем `a b-c` .
   Это сопоставление можно настроить для каждой базы данных после подключения. Дополнительные сведения см. в разделе [Сопоставление исходных и целевых баз данных](mapping-source-and-target-databases-accesstosql.md) .

5. В раскрывающемся меню **Проверка подлинности** выберите тип проверки подлинности, который будет использоваться для соединения. Чтобы использовать текущую учетную запись Windows, выберите **Проверка подлинности Windows**. Чтобы использовать имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, выберите **SQL Server проверка подлинности**, а затем укажите имя пользователя и пароль.

6. Для безопасного подключения добавляются два элемента управления: флажок **Шифровать соединение** и **TrustServerCertificate** . Флажок только при **шифровании подключения** установлен **TrustServerCertificate** . Если установлен флажок **Шифровать соединение** (true) и **TrustServerCertificate** (false), то будет проверять [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSL-сертификат. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы убедиться в этом, сертификат должен быть установлен на стороне клиента, а также на стороне сервера.

7. Нажмите кнопку **Соединить**.

> [!IMPORTANT]
> Хотя вы можете подключаться к более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , по сравнению с версией, выбранной при создании проекта миграции, преобразование объектов базы данных определяется целевой версией проекта, а не версией, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к которой вы подключены.

## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server

Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы изменяются после подключения, можно синхронизировать метаданные с сервером.

Чтобы синхронизировать метаданные SQL Server, **SQL Server Обозреватель метаданных**, щелкните правой кнопкой мыши **базы данных** и выберите **синхронизировать с базой данных**.

## <a name="reconnecting-to-sql-server"></a>Повторное подключение к SQL Server

Подключение будет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оставаться активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока объекты базы данных не будут загружены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не перенесены.

Процедура повторного подключения к совпадает с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] процедурой установки соединения.

## <a name="next-steps"></a>Next Steps

Если вы хотите настроить сопоставление между исходной и целевой базами данных, см. раздел [сопоставление исходной и целевой баз данных](mapping-source-and-target-databases-accesstosql.md) в противном случае следующим шагом является преобразование объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис с помощью инструкции [Convert Objects](converting-access-database-objects-accesstosql.md).

## <a name="see-also"></a>См. также:

[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)
