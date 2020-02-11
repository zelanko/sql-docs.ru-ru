---
title: Установка компонентов SSMA на SQL Server (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1fbc3a8f74b21bd5a53bdd874b5c41ef522e29f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029012"
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Установка компонентов SSMA в SQL Server (SybaseToSQL)
Помимо установки SSMA, для использования переноса данных на стороне сервера необходимо также установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. К этим компонентам относится пакет расширений SSMA, который поддерживает миграцию данных, и поставщики Sybase для обеспечения подключения между серверами.  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA для пакета расширения Sybase  
Пакет расширений SSMA добавляет базы данных, **сисдб** и **ssmatesterdb_syb**, к указанному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. База данных **сисдб** содержит таблицы и хранимые процедуры, необходимые для переноса данных. База данных **ssmatester_syb** содержит **ssma_sybase_utilities**схемы, в которой создаются объекты (таблицы, триггеры, представления), используемые компонентом SSMA Tester.  
  
Кроме того, при переносе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в SSMA создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента, когда для переноса данных используется модуль миграции данных на стороне сервера.  
  
### <a name="installing-the-extension-pack"></a>Установка пакета расширений  
Пакет расширений можно установить в любое время перед переносом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Чтобы установить пакет расширений, необходимо быть членом роли сервера sysadmin на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Установка пакета расширений**  
  
1.  Скопируйте SSMA для пакета расширения Sybase. *n*. Install. exe, где *n* — номер сборки, на компьютер, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Дважды щелкните SSMA для пакета расширения Sybase. *n*. Install. exe.  
  
3.  На странице приветствия нажмите кнопку **Далее**.  
  
4.  На странице Лицензионное соглашение ознакомьтесь с лицензионным соглашением. Если вы согласны, установите флажок **я принимаю условия лицензионного соглашения** и нажмите кнопку **Далее**.  
  
5.  На странице Выбор типа установки выберите вариант **Обычная**.  
  
6.  На странице все готово для установки нажмите кнопку **установить**.  
  
7.  На странице завершено первое действие установки нажмите кнопку **Далее**.  
  
    Появится новое диалоговое окно, в котором будет выбран экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для установки пакета расширений.  
  
8.  Выберите экземпляр, на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] котором будут перенесены базы данных ASE, и нажмите кнопку **Далее**.  
  
    Имя экземпляра по умолчанию совпадает с именем компьютера. За именованными экземплярами будет следовать обратная косая черта и имя экземпляра.  
  
9. На странице Параметры соединения выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    При проверке подлинности Windows будут использоваться учетные данные Windows для входа на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности необходимо ввести имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа и пароль.  
  
10. На странице Manage Server (Управление сервером) выберите **установить служебные базы данных** *n*, где *n* — номер версии, а затем нажмите кнопку **Далее**.  
  
    Создается база данных **сисдб** , а хранимые процедуры создаются в этой базе данных.  
  
    Если установлен флажок **установить базу данных тестировщика** , **ssmatesterdb_syb** будет создана база данных тестеров.  
  
11. Чтобы установить служебные программы на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выберите **вернуться к экземплярам**, а затем нажмите кнопку **Далее**. Чтобы выйти из мастера, нажмите кнопку **выход**.  
  
### <a name="sql-server-database-objects"></a>SQL Server объекты базы данных  
После установки пакета расширений вы увидите таблицу **ssma_syb. bcp_migration_packages** в базе данных **сисдб** . Вы также увидите следующие хранимые процедуры:  
  
-   **bcp_clean_migration_data**  
  
-   **bcp_ensure_message_table**  
  
-   **bcp_insert_new_message**  
  
-   **bcp_post_process**  
  
-   **bcp_read_new_migration_messages**  
  
-   **bcp_save_migration_package**  
  
-   **bcp_smart_truncate**  
  
-   **bcp_start_migration_process**  
  
-   **get_jobstep_info**  
  
-   **stop_agent_process**  
  
Каждый раз при переносе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SSMA создает задание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента. Эти задания называются **ssma_syb пакет переноса данных {GUID}** и отображаются в узле [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в папке задания.  
  
## <a name="sybase-providers"></a>Поставщики Sybase  
При переносе данных из ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Microsoft/SQL Azure данные переносятся непосредственно между ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure. Он не проходит через SSMA, так как это замедляет перенос данных.  
  
### <a name="installing-the-sybase-providers"></a>Установка поставщиков Sybase  
Следующие инструкции содержат основные шаги по установке поставщиков Sybase. Точные инструкции будут различаться в зависимости от версии программы установки Sybase.  
  
> [!IMPORTANT]  
> Перед запуском программы установки убедитесь, что вы не нарушаете Лицензионное соглашение.  
  
1.  Запустите программу установки ASE Sybase.  
  
2.  Выберите Выборочная установка.  
  
3.  На странице Выбор компонентов выберите поставщики данных ODBC, OLE DB и ADO.NET.  
  
4.  Проверьте выбранные компоненты и нажмите кнопку **"Готово"** , чтобы установить поставщик данных.  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для клиента Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Миграция баз данных Sybase ASE в SQL Server Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
