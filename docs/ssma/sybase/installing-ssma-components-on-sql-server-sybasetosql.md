---
title: Установка компонентов SSMA на SQL Server (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97c0e5dc529a6563212dc3ddedce5014ccfd463a
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Установка компонентов SSMA на SQL Server (SybaseToSQL)
Помимо установки SSMA, для использования сервера миграцию данных, необходимо установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эти компоненты включают пакет расширения SSMA, поддерживающей переноса данных и поставщики Sybase, чтобы включить возможность подключения сервера к серверу.  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA для пакета расширения Sybase  
Пакет расширения SSMA добавляет баз данных, **sysdb** и **ssmatesterdb_syb**, для указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. **Sysdb** база данных содержит таблицы и хранимые процедуры, необходимые для переноса данных. **Ssmatester_syb** база данных содержит схему **ssma_sybase_utilities**, в которой создаются объекты (таблицы, триггеры, представления), используется компонентом инженер-испытатель SSMA.  
  
Кроме того, при переносе данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] заданий агента, когда модуль переноса данных стороне сервера используется для переноса данных.  
  
### <a name="installing-the-extension-pack"></a>Установка пакета расширения  
Пакет расширения можно установить любое время, прежде чем переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!IMPORTANT]  
> Установка пакета расширения, необходимо быть членом роли сервера sysadmin на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Чтобы установить пакет расширения**  
  
1.  Скопируйте SSMA для пакета расширения Sybase. *n*. Install.exe, где *n* — номер сборки, на компьютер, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
2.  Дважды щелкните SSMA для пакета расширения Sybase. *n*. Install.exe.  
  
3.  На странице приветствия нажмите кнопку **Далее**.  
  
4.  На странице Лицензионное соглашение прочитайте лицензионное соглашение. Если вы согласны, установите **я принимаю условия лицензионного соглашения** флажок и нажмите кнопку **Далее**.  
  
5.  На странице Выбор типа установки щелкните **обычные**.  
  
6.  На странице готовности к установке, нажмите кнопку **установить**.  
  
7.  На завершено странице первый шаг установки, нажмите кнопку **Далее**.  
  
    Появится новое диалоговое окно, в котором можно выбрать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для установки пакета расширения.  
  
8.  Выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] где вы будет миграция ASE баз данных, а затем нажмите кнопку **Далее**.  
  
    Экземпляр по умолчанию имеет имя, совпадающее с именем компьютера. Именованные экземпляры будут следовать обратную косую черту и имя экземпляра.  
  
9. На странице Параметры подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] имя входа и пароль.  
  
10. На странице «Управление сервером» выберите **установки базы данных программы** *n*, где *n* номер версии, а затем нажмите кнопку **Далее**.  
  
    **Sysdb** создания базы данных и хранимые процедуры создаются в этой базе данных.  
  
    Если **установки базы данных тест-инженер** флажок тест-инженер **ssmatesterdb_syb** будет создана база данных.  
  
11. Чтобы установить эти программы на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]выберите **вернуться к экземплярам**и нажмите кнопку **Далее**. Чтобы завершить работу мастера, нажмите кнопку **выхода**.  
  
### <a name="sql-server-database-objects"></a>Объекты базы данных SQL Server  
После установки пакета расширения, вы будете см. в разделе **ssma_syb.bcp_migration_packages** в таблицу **sysdb** базы данных. Кроме того, вы увидите следующие хранимые процедуры:  
  
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
  
Каждый раз при переносе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] задания агента. Эти задания называются **ssma_syb данных миграции пакета {GUID}**и отображаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] узел агента [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] в папку «задания».  
  
## <a name="sybase-providers"></a>Поставщики Sybase  
При переносе данных из ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]выполняет миграцию данных SQL Azure, напрямую между ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure. Он не проходит через SSMA, так как это может замедлить процесс переноса данных.  
  
### <a name="installing-the-sybase-providers"></a>Установка поставщиков Sybase  
Приведенные ниже инструкции описаны шаги базовой установки для установки поставщиков Sybase. Точные инструкции будут отличаться в зависимости от версии программы установки Sybase.  
  
> [!IMPORTANT]  
> Перед запуском программы установки проверьте, не нарушают обязательств по лицензионным соглашениям.  
  
1.  Запустите программу установки Sybase ASE.  
  
2.  Выберите пользовательские настройки.  
  
3.  На странице выбора компонентов выберите поставщиков данных ODBC, OLE DB и ADO.NET.  
  
4.  Проверьте выбранные компоненты и нажмите кнопку **Готово** Установка поставщика данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для клиента Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Миграция баз данных Sybase ASE в SQL Server — Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
