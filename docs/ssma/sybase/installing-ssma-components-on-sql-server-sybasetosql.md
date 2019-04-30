---
title: Установка компонентов SSMA в SQL Server (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6121c75390e7493052a16b2e898eac69283e41ec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63294569"
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Установка компонентов SSMA в SQL Server (SybaseToSQL)
Помимо установки SSMA, для использования миграции данных на стороне сервера, необходимо также установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти компоненты включают пакет расширений SSMA, которая поддерживает перенос данных и поставщики Sybase, чтобы обеспечить подключение между серверами.  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA для Sybase Extension Pack  
Пакет расширений SSMA добавляет баз данных, **sysdb** и **ssmatesterdb_syb**, для указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Sysdb** база данных содержит таблицы и хранимые процедуры, которые необходимы для переноса данных. **Ssmatester_syb** содержит схему, **ssma_sybase_utilities**, в которой создаются объекты (таблицы, триггеры, представления), используемые компонентом тест-инженер SSMA.  
  
Кроме того, при переносе данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента, когда модуль переноса данных на стороне сервера используется для переноса данных.  
  
### <a name="installing-the-extension-pack"></a>Установка пакета расширения  
Пакет расширений можно установить любое время, прежде чем переносить данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Чтобы установить пакет расширения, необходимо быть членом роли сервера sysadmin на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Чтобы установить пакет расширений**  
  
1.  Скопируйте SSMA для Sybase Extension Pack. *n*. Install.exe, где *n* — номер сборки, на компьютер, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Дважды щелкните SSMA для Sybase Extension Pack. *n*. Install.exe.  
  
3.  На странице приветствия нажмите кнопку **Далее**.  
  
4.  На странице "лицензионное соглашение" Прочитайте лицензионное соглашение. Если вы согласны, установите **я принимаю условия лицензионного соглашения** флажок и нажмите кнопку **Далее**.  
  
5.  На странице "Выбор типа установки" нажмите кнопку **обычные**.  
  
6.  На странице готовности к установке, нажмите кнопку **установить**.  
  
7.  На Completed странице первый шаг установки, нажмите кнопку **Далее**.  
  
    Появится новое диалоговое окно, в котором можно выбрать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для установки пакета расширения.  
  
8.  Выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] где вам будет миграции баз данных ASE, а затем нажмите кнопку **Далее**.  
  
    Экземпляр по умолчанию имеет имя, совпадающее с именем компьютера. Именованные экземпляры будут следовать обратную косую черту и имя экземпляра.  
  
9. На странице Параметры подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль.  
  
10. На странице "Управление сервером", выберите **установить базы данных служебных программ** *n*, где *n* — это номер версии, а затем нажмите кнопку **Далее**.  
  
    **Sysdb** создания базы данных и хранимые процедуры создаются в этой базе данных.  
  
    Если **установить базы данных тест-инженер** флажок тест-инженер **ssmatesterdb_syb** будет создана база данных.  
  
11. Чтобы установить служебные программы с другим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выберите **вернуться к экземплярам**и нажмите кнопку **Далее**. Чтобы выйти из мастера, нажмите кнопку **выйти из**.  
  
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
  
Каждый раз, переносить данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента. Эти задания называются **ssma_syb данных миграции пакета {GUID}** и отображаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] узел агента [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в папку «задания».  
  
## <a name="sybase-providers"></a>Поставщики Sybase  
При переносе данных из ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполняет миграцию данных SQL Azure, непосредственно между ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Azure. Он не проходит через SSMA, так как это может замедлить процесс переноса данных.  
  
### <a name="installing-the-sybase-providers"></a>Установка поставщиков Sybase  
Ниже описаны шаги базовой установки для установки поставщиков Sybase. Точные инструкции будут различаться в зависимости от версии программы установки Sybase.  
  
> [!IMPORTANT]  
> Перед запуском программы установки проверьте, не нарушают вашей лицензионных соглашений.  
  
1.  Запустите программу установки Sybase ASE.  
  
2.  Выбор пользовательской установки.  
  
3.  На странице выбора компонентов выберите поставщики данных ODBC, OLE DB и ADO.NET.  
  
4.  Проверьте выбранные компоненты и нажмите кнопку **Готово** для установки поставщика данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для Sybase клиента &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Миграция баз данных Sybase ASE в SQL Server — база данных Azure SQL &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
