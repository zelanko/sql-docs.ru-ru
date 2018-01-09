---
title: "Работа с данными SQL Server с помощью R (SQL и R глубокое погружение) | Документы Microsoft"
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 0a3d7ba0-4113-4cde-9645-debba45cae8f
caps.latest.revision: "20"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: adf32a43f54ab670c096c04180fa6638fed64e8f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="work-with-sql-server-data-using-r-sql-and-r-deep-dive"></a>Работа с данными SQL Server, с помощью R (SQL и R глубокое погружение)

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии настройки среды и добавить данные, необходимые для обучения моделей и выполните некоторые сводки по данным. В рамках процесса необходимо выполнить следующие задачи:
  
- создадите базу данных, в которой будут храниться данные для обучения и оценки двух моделей R;
  
- создадите учетную запись (пользователя Windows или имя входа SQL), которая будет использоваться для обмена данными между рабочей станцией и сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;
  
- создадите источники данных в R для работы с данными и объектами базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;
  
- используете источник данных R для загрузки данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];
  
- используете язык R для получения списка переменных и изменения метаданных таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;
  
- создадите контекст вычисления для удаленного выполнения кода на языке R;
  
- (Необязательно) Включите трассировку в контексте удаленного вычислений.
  
## <a name="create-the-database-and-user"></a>Создание базы данных и пользователя

В этом пошаговом руководстве, необходимо создать новую базу данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]и добавьте имя входа SQL с разрешениями для записи и чтения данных и для запуска сценариев R.

> [!NOTE]
> Если выполняется только чтение данных, учетная запись, которая запускает сценарии R требуются разрешения SELECT (**db_datareader** роли) в указанной базе данных. Тем не менее в этом учебнике необходимо иметь права доступа администратора DDL Подготовка базы данных и создание таблицы для сохранения результатов оценки.
> 
> Кроме того Если вы не являетесь владельцем базы данных, необходимо разрешение EXECUTE ANY EXTERNAL SCRIPT для выполнения R-скриптов.

1. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]выберите экземпляр, в котором включены службы [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , щелкните правой кнопкой мыши элемент **базы данных**и выберите пункт **Создать базу данных**.
  
2. Введите имя новой базы данных. Вы можете использовать любое имя, но не забудьте внести соответствующие изменения во все скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] и R в этом пошаговом руководстве.
  
    > [!TIP]
    > Чтобы увидеть новое имя базы данных, щелкните правой кнопкой мыши элемент **Базы данных** и выберите пункт **Обновить** .
  
3. Щелкните **Создать запрос**и измените контекст базы данных на master.
  
4. В новом окне **Запрос** выполните приведенные ниже команды, чтобы создать учетные записи пользователей и назначить их базе данных, используемой в этом учебнике. При необходимости измените имя базы данных.
  
**Пользователь Windows**
  
```SQL
 -- Create server user based on Windows account
USE master
GO
CREATE LOGIN [<DOMAIN>\<user_name>] FROM WINDOWS WITH DEFAULT_DATABASE=[DeepDive]

 --Add the new user to tutorial database
USE [DeepDive]
GO
CREATE USER [<user_name>] FOR LOGIN [<DOMAIN>\<user_name>] WITH DEFAULT_SCHEMA=[db_datareader]
```

**Имя входа SQL**

```SQL
-- Create new SQL login
USE master
GO
CREATE LOGIN DDUser01 WITH PASSWORD='<type password here>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;

-- Add the new SQL login to tutorial database
USE [DeepDive]
GO
CREATE USER [DDUser01] FOR LOGIN [DDUser01] WITH DEFAULT_SCHEMA=[db_datareader]
```

5. Чтобы проверить, был ли создан пользователь, выберите новую базу данных, а затем разверните узлы **Безопасность**и **Пользователи**.

## <a name="troubleshooting"></a>Устранение неполадок

В этом разделе перечислены некоторые распространенные проблемы, которые могут возникнуть в процессе настройки базы данных.

- **Как проверить подключение к базе данных и запросы SQL?**
  
    Перед выполнением кода на языке R с помощью сервера может потребоваться проверить, доступна ли база данных из среды разработки R. [Обозреватель сервера Visual Studio](https://msdn.microsoft.com/library/x603htbk.aspx) и [среда SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) являются бесплатными средствами с эффективными возможностями подключения к базам данных и функциями управления.
  
    Если вы не хотите устанавливать дополнительные средства управления базами данных, то можете создать тестовое подключение к экземпляру SQL Server с помощью компонента [Администратор источников данных ODBC](https://msdn.microsoft.com/library/ms714024.aspx) на панели управления. Если база данных настроена правильно и вы ввели верные имя пользователя и пароль, то вы увидите созданную базу данных и сможете выбрать ее в качестве базы данных по умолчанию.
  
    Если вы не можете подключиться к базе данных, проверьте, включены ли удаленные подключения для сервера и включен ли протокол именованных каналов. В этой статье приведены дополнительные советы по устранению неполадок: [Устранение неполадок подключения к SQL Server Database Engine](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Почему имя таблицы имеет префикс datareader?**
  
    При указании схемы по умолчанию для этого пользователя с **db_datareader**, все таблицы и другие новые объекты, созданные этим пользователем начинаются с префикса *схемы* имя. Схема напоминает папку, которую можно добавить к базе данных для упорядочения объектов. Схема также определяет права пользователя в базе данных.
  
    Когда схема связывается с одного имени конкретного пользователя, пользователь получает _владельца схемы_. Когда вы создаете объект, он всегда создается в вашей собственной схеме, если вы специально не укажете, что он должен быть создан в другой схеме.
  
    Например, если создать таблицу с именем `*`TestData`, and your default schema is **db\_datareader**, the table is created with the name `.db_datareader < имя_базы_данных >. TestData ".
  
    По этой причине база данных может содержать несколько таблиц с одинаковыми именами, если они относятся к разным схемам.
   
    Если вам нужны для таблицы и не указать схему, сервер базы данных ищет схемы, что вы являетесь владельцем. Поэтому нет необходимости указывать имя схемы при доступе к таблицам в схеме, связанной в вашим именем входа.
  
- **У меня нет прав DDL. Могу ли я работать с учебником?**
  
    Да. Однако вам нужно будет предварительно попросить кого-нибудь загрузить данные в таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а затем пропустить разделы, в которых требуется создать таблицы. Функции, которые требуются привилегии DDL вызываются в учебнике по возможности.

    Кроме того обратитесь к администратору, чтобы предоставить вам разрешения EXECUTE ANY EXTERNAL SCRIPT. Он необходим для выполнения скриптов R, удаленных или с помощью `sp_execute_external_script`.

## <a name="next-step"></a>Следующий шаг

[Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)

## <a name="overview"></a>Обзор

[Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)



