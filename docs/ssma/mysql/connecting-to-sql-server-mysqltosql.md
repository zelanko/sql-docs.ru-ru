---
title: Подключение к SQL Serverу (MySQLToSQL) | Документация Майкрософт
description: Узнайте, как подключиться к целевому экземпляру SQL Server для переноса баз данных MySQL. SSMA получает метаданные о базах данных в SQL Server.
ms.prod: sql
ms.custom: ''
ms.date: 11/16/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: c004f4ced6bad2b6db45f4be56e442a10965a514
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870241"
---
# <a name="connecting-to-sql-server-mysqltosql"></a>Подключение к SQL Server (MySQLToSQL)

Чтобы перенести базы данных MySQL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо подключиться к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При подключении SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отображает метаданные базы данных в **обозревателе метаданных SQL Server**. SSMA хранит сведения о экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , к которому вы подключены, но не хранят пароли.

Подключение будет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оставаться активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока объекты базы данных не будут загружены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не перенесены.

Метаданные экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не синхронизируются автоматически. Вместо этого для обновления метаданных в **SQL Server обозревателе метаданных** необходимо вручную обновить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданные. Дополнительные сведения см. в подразделе "синхронизация метаданных SQL Server" Далее в этом разделе.

## <a name="required-sql-server-permissions"></a>Обязательные SQL Server разрешения

Для учетной записи, используемой для подключения к, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуются другие разрешения в зависимости от действий, выполняемых учетной записью.

- Чтобы преобразовать объекты MySQL в [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, обновить метаданные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или сохранить преобразованный синтаксис в скрипты, учетная запись должна иметь разрешение на вход в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

- Чтобы загрузить объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , учетная запись должна быть членом роли базы данных **db_ddladmin** .

- Для переноса данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетную запись должны быть:
  - Член роли базы данных **db_owner** , если используется модуль миграции данных на стороне клиента.
  - Член роли сервера **sysadmin** , если используется модуль миграции данных на стороне сервера. Это необходимо для создания `CmdExec` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] шага задания агента во время переноса данных для запуска средства SSMAного копирования.
    > [!NOTE]
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Учетные записи-посредники агентов не поддерживаются при переносе данных на стороне сервера.

## <a name="establishing-a-sql-server-connection"></a>Установка подключения SQL Server

Перед преобразованием объектов базы данных MySQL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис необходимо установить соединение с экземпляром, на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] котором требуется перенести базу данных или базы MySQL.

При определении свойств соединения также указывается база данных, в которую будут перенесены объекты и данные. Это сопоставление можно настроить на уровне схемы MySQL после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. [в разделе Сопоставление баз данных MySQL с SQL Server схемами &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md).

> [!IMPORTANT]
> Прежде чем пытаться подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , убедитесь, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает и может принимать подключения.

Для подключения к SQL Server:

1. В меню **файл** выберите команду **подключиться к SQL Server** (этот параметр включен после создания проекта).
   Если ранее вы подключились к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , имя команды будет **повторно подключено к SQL Server**.

2. В диалоговом окне Соединение введите или выберите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
   - При подключении к экземпляру по умолчанию на локальном компьютере можно ввести `localhost` или точку ( `.` ).
   - При подключении к экземпляру по умолчанию на другом компьютере введите имя компьютера.
   - При подключении к именованному экземпляру на другом компьютере введите имя компьютера, затем обратную косую черту, а затем имя экземпляра, например `MyServer\MyInstance` .

3. Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для приема подключений по нестандартному порту, введите номер порта, используемый для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединений, в поле **порт сервера** . Для экземпляра по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] номер порта по умолчанию — 1433. Для именованных экземпляров SSMA попытается получить номер порта из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы браузера.

4. В поле **Проверка подлинности** выберите тип проверки подлинности, который будет использоваться для соединения. Чтобы использовать текущую учетную запись Windows, выберите **Проверка подлинности Windows**. Чтобы использовать имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, выберите **SQL Server проверка подлинности**, а затем укажите имя входа и пароль.

5. Для безопасного подключения добавляются два элемента управления: флажки **Шифровать соединение** и **TrustServerCertificate** . Флажок **TrustServerCertificate** отображается только при установленном **шифровании соединения** . Если флажок **Шифровать соединение** установлен (true) и **TrustServerCertificate** не установлен (false), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сертификат SSL будет проверен. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы убедиться в этом, сертификат должен быть установлен на стороне клиента, а также на стороне сервера.

6. Нажмите кнопку **Соединить**.

> [!IMPORTANT]
> Хотя вы можете подключаться к более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , по сравнению с версией, выбранной при создании проекта миграции, преобразование объектов базы данных определяется целевой версией проекта, а не версией, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к которой вы подключены.

## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server

Метаданные о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базах данных не обновляются автоматически. Метаданные в **SQL Server обозревателе метаданных** являются моментальным снимком метаданных при первом соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или при последнем обновлении метаданных вручную. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объекта базы данных. Для синхронизации метаданных:

1. Убедитесь, что вы подключены к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

2. В **SQL Server обозревателе метаданных** установите флажок рядом с базой данных или схемой базы данных, которую требуется обновить.
   Например, чтобы обновить метаданные для всех баз данных, установите флажок рядом с пунктом **databases (базы данных**).

3. Щелкните правой кнопкой мыши **базы данных** или отдельную базу данных или схему базы данных, а затем выберите **синхронизировать с базой данных**.

## <a name="next-step"></a>Следующий шаг

Следующий шаг миграции зависит от потребностей проекта:

- Сведения о настройке сопоставления между схемами MySQL и SQL Server базами данных и схемами см. в разделе [Сопоставление баз данных MySQL с SQL Server схемами &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md).
- Сведения о настройке параметров конфигурации для проектов см. в разделе [Установка параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md).
- Сведения о настройке сопоставления исходных и целевых типов данных см. в разделе [Сопоставление типов данных MySQL и SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md).
- Если не нужно выполнять какие – либо из этих задач, можно преобразовать определения объектов базы данных MySQL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определения объектов. Дополнительные сведения см. в статье [Преобразование баз данных MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md).

## <a name="see-also"></a>См. также:

[Перенос баз данных MySQL в SQL Server базы данных SQL Azure &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)
