---
description: Установка компонентов SSMA на SQL Server (SybaseToSQL)
title: Установка компонентов SSMA на SQL Server (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/14/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 33b5663e7693de8c031f2b39c0436a771920be56
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88372370"
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Установка компонентов SSMA на SQL Server (SybaseToSQL)

Помимо установки SSMA, для использования переноса данных на стороне сервера необходимо также установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . К этим компонентам относится пакет расширений SSMA, который поддерживает миграцию данных, и поставщики Sybase для обеспечения подключения между серверами.

## <a name="ssma-for-sybase-extension-pack"></a>SSMA для пакета расширения Sybase

Пакет расширений SSMA добавляет базы данных, **сисдб** и **ssmatesterdb_syb**, к указанному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . База данных **сисдб** содержит таблицы и хранимые процедуры, необходимые для переноса данных. База данных **ssmatester_syb** содержит **ssma_sybase_utilities**схемы, в которой создаются объекты (таблицы, триггеры, представления), используемые компонентом SSMA Tester.

Кроме того, при переносе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSMA создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента, когда для переноса данных используется модуль миграции данных на стороне сервера.

### <a name="prerequisites"></a>Предварительные требования

Перед установкой SSMA для серверных компонентов Sybase [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Убедитесь, что система соответствует следующим требованиям.

- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр установлен.
- Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версия 4.7.2 или более поздняя. Его можно получить в [центре разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).
- Поставщик Sybase OLE DB/ADO.Net/ODBC и подключение к серверу базы данных SAP ASE, содержащему базы данных, которые необходимо перенести. Поставщики можно установить на носителе с продуктом SAP ASE. Дополнительные сведения о подключении см. [в статье подключение к SYBASE ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Служба браузера должна быть запущена во время установки. Используется для заполнения списка экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в мастере установки. Службу браузера можно отключить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после установки.

  > [!NOTE]
  > Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Служба браузера запущена, но список экземпляров в программе установки по-прежнему не отображается, необходимо разблокировать UDP-порт 1434. Вы можете использовать брандмауэр Windows, чтобы временно разблокировать порт, или временно отключить брандмауэр Windows. Также может потребоваться временное отключение антивирусного по. После установки обязательно включите брандмауэры и антивирусное по.

### <a name="installing-the-extension-pack"></a>Установка пакета расширений

Пакет расширений можно установить в любое время перед переносом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

> [!IMPORTANT]
> Чтобы установить пакет расширений, необходимо быть членом роли сервера sysadmin на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Чтобы установить пакет расширений, выполните следующие действия.

1. Скопируйте **SSMAforSybaseExtensionPack_*n*. msi**, где *n* — номер сборки, на компьютер, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
2. Дважды щелкните **SSMAforSybaseExtensionPack_*n*. msi**.
3. На странице **приветствия** нажмите кнопку **Далее**.
4. На странице Лицензионное **соглашение** ознакомьтесь с лицензионным соглашением. Если вы согласны, выберите параметр **я принимаю условия соглашения** , а затем нажмите кнопку **Далее**.
5. На странице **Выбор типа установки** выберите вариант **Обычная**.
6. На странице **Все готово для установки** нажмите **Установить**.
7. На странице **завершено первое действие установки** нажмите кнопку **Далее**.

   Появится новое диалоговое окно, в котором будет выбран экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для установки пакета расширений.

8. Выберите экземпляр, на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] котором будут перенесены базы данных SAP ASE, и нажмите кнопку **Далее**.

   Имя экземпляра по умолчанию совпадает с именем компьютера. За именованными экземплярами будет следовать обратная косая черта и имя экземпляра.

9. На странице Подключение выберите метод проверки подлинности и нажмите кнопку **Далее**.

   При проверке подлинности Windows будут использоваться учетные данные Windows для входа на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При выборе проверки подлинности сервера необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль.

10. На следующем шаге необходимо задать пароль для главного ключа, который будет использоваться для шифрования любых конфиденциальных данных, хранящихся в базе данных пакета расширений при переносе данных на стороне сервера. Укажите надежный пароль и нажмите кнопку **Далее**.

11. На следующей странице выберите **установить служебные программы база данных *n* и установите библиотеки пакетов расширений**, где *n* — номер версии. Если вы планируете использовать функцию "тест-инженер", установите флажок **установить базу данных тестировщика** и нажмите кнопку **Далее**.

    База данных **сисдб** создается с таблицами и хранимыми процедурами, необходимыми для переноса данных (используя модуль миграции данных на стороне сервера) в этой базе данных.

    Если установлен флажок **установить базу данных тестировщика** , будет создана **ssmatesterdb_syb** база данных.

12. После завершения установки появится запрос на подтверждение установки служебной базы данных на другом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выберите **Да**, а затем нажмите кнопку **Далее**или закрыть мастер, выберите **нет** и нажмите кнопку **выход**.

### <a name="sql-server-database-objects"></a>SQL Server объекты базы данных

После установки пакета расширений вы увидите таблицу **ssma_syb. bcp_migration_packages** в базе данных **сисдб** . Вы также увидите следующие хранимые процедуры:

- `bcp_clean_migration_data`
- `bcp_ensure_message_table`
- `bcp_insert_new_message`
- `bcp_post_process`
- `bcp_read_new_migration_messages`
- `bcp_save_migration_package`
- `bcp_smart_truncate`
- `bcp_start_migration_process`
- `get_jobstep_info`
- `stop_agent_process`

Каждый раз при переносе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSMA создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Задание агента. Эти задания называются **ssma_syb пакет переноса данных {GUID}** и отображаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] узле агент [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в папке задания.  

## <a name="sybase-providers"></a>Поставщики Sybase

При использовании переноса данных на стороне сервера для перемещения данных из SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данные переносятся непосредственно между SAP ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Он не проходит через SSMA, так как это замедляет перенос данных.

### <a name="installing-the-sybase-providers"></a>Установка поставщиков Sybase

Следующие инструкции содержат основные шаги по установке поставщиков Sybase. Точные инструкции будут различаться в зависимости от версии программы установки Sybase.

> [!IMPORTANT]
> Перед запуском программы установки убедитесь, что вы не нарушаете Лицензионное соглашение.

1. Запустите программу установки ASE Sybase.
2. Выберите Выборочная установка.
3. На странице Выбор компонентов выберите поставщики данных ODBC, OLE DB и ADO.NET.
4. Проверьте выбранные компоненты и нажмите кнопку **"Готово"** , чтобы установить поставщик данных.

## <a name="see-also"></a>См. также раздел

- [Установка SSMA для клиента Sybase](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)
- [Миграция баз данных Sybase ASE в базу данных SQL Azure SQL Server](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)
