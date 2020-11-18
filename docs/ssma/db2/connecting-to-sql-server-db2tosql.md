---
description: Подключение к SQL Server (DB2ToSQL)
title: Подключение к SQL Serverу (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 11/16/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b59803cb-3cc6-41cc-8553-faf90851410e
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5b039840ea7e010597de05ffb524eb5f568b0624
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870664"
---
# <a name="connecting-to-sql-server-db2tosql"></a>Подключение к SQL Server (DB2ToSQL)

Чтобы перенести базы данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо подключиться к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При подключении SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отображает метаданные базы данных в **обозревателе метаданных SQL Server**. SSMA хранит сведения о том, к какому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вы подключены, но не хранят пароли.

Подключение будет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оставаться активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока объекты базы данных не будут загружены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не перенесены.

Метаданные экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не синхронизируются автоматически. Вместо этого для обновления метаданных в **SQL Server обозревателе метаданных** необходимо вручную обновить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданные. Дополнительные сведения см. в подразделе "синхронизация метаданных SQL Server" Далее в этом разделе.

## <a name="required-sql-server-permissions"></a>Обязательные SQL Server разрешения

Для учетной записи, используемой для подключения к, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуются другие разрешения в зависимости от действий, выполняемых учетной записью.

- Чтобы преобразовать объекты DB2 в [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, обновить метаданные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или сохранить преобразованный синтаксис в скрипты, учетная запись должна иметь разрешение на вход в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

- Чтобы загрузить объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , учетная запись должна быть членом роли сервера **db_ddladmin** .

- Чтобы перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , учетная запись должна быть членом роли базы данных **db_owner** .

- Для запуска кода, созданного SSMA, учетная запись должна иметь `EXECUTE` разрешения для всех определяемых пользователем функций в схеме **ssma_db2** целевой базы данных. Эти функции предоставляют эквивалентные функции системных функций DB2 и используются преобразованными объектами.

## <a name="establishing-a-sql-server-connection"></a>Установка подключения SQL Server

Перед преобразованием объектов базы данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис необходимо установить соединение с экземпляром, на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] котором требуется перенести базу данных или базы DB2.

При определении свойств соединения также указывается база данных, в которую будут перенесены объекты и данные. Это сопоставление можно настроить на уровне схемы DB2 после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. [в разделе сопоставление схем DB2 с SQL Server схемами &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).

> [!IMPORTANT]
> Прежде чем пытаться подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , убедитесь, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает и может принимать подключения.  
  
Чтобы подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :

1. В меню **файл** выберите **подключиться к SQL Server**.
   Если ранее вы подключились к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , имя команды будет **повторно подключено к SQL Server**.

2. В диалоговом окне Соединение введите или выберите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
   - При подключении к экземпляру по умолчанию на локальном компьютере можно ввести `localhost` или точку ( `.` ).
   - При подключении к экземпляру по умолчанию на другом компьютере введите имя компьютера.
   - При подключении к именованному экземпляру на другом компьютере введите имя компьютера, затем обратную косую черту, а затем имя экземпляра, например `MyServer\MyInstance` .

3. Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для приема подключений по нестандартному порту, введите номер порта, используемый для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединений, в поле **порт сервера** . Для экземпляра по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] номер порта по умолчанию — 1433. Для именованных экземпляров SSMA попытается получить номер порта из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы браузера.

4. В поле **база данных** введите имя целевой базы данных.
   Этот параметр недоступен при повторном подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

5. В поле **Проверка подлинности** выберите тип проверки подлинности, который будет использоваться для соединения. Чтобы использовать текущую учетную запись Windows, выберите **Проверка подлинности Windows**. Чтобы использовать имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, выберите **SQL Server проверка подлинности**, а затем укажите имя входа и пароль.

6. Для безопасного подключения добавляются два элемента управления: флажки **Шифровать соединение** и **TrustServerCertificate** . Флажок **TrustServerCertificate** отображается только при установленном **шифровании соединения** . Если флажок **Шифровать соединение** установлен (true) и **TrustServerCertificate** не установлен (false), он будет проверять SQL Server SSL-сертификат. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы убедиться в этом, сертификат должен быть установлен на стороне клиента, а также на стороне сервера.

7. Нажмите кнопку **Соединить**.

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

- Сведения о настройке сопоставления между схемами DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базами данных и схемами см. в разделе [сопоставление схем db2 с SQL Server схемами &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).
- Чтобы настроить параметры конфигурации для проектов, см. раздел [Project Settings &#40;Conversion&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md) and Related.
- Сведения о настройке сопоставления исходных и целевых типов данных см. в разделе [Сопоставление типов данных DB2 и SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).
- Если не нужно выполнять какие – либо из этих задач, можно преобразовать определения объектов базы данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определения объектов. Дополнительные сведения см. в разделе [Преобразование схем DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).

## <a name="see-also"></a>См. также:

[Перенос баз данных DB2 в SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)
