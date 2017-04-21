---
title: "Просмотр или изменение зарегистрированных фильтров и средств разбиения текста на слова | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full-text search [SQL Server], word breakers
- full-text search [SQL Server], filters
- filters [full-text search]
- word breakers [full-text search]
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2032d8aaaa75352d64aa4ed19ec53670afe6d8a7
ms.lasthandoff: 04/11/2017

---
# <a name="view-or-change-registered-filters-and-word-breakers"></a>Просмотр или изменение зарегистрированных фильтры и разделители слов
  После того как в системе была произведена установка или удаление средств разбиения по словам или фильтров, автоматического внесения изменений на экземплярах сервера не происходит. В данном разделе описано, как можно просмотреть зарегистрированные в данный момент средства разбиения по словам и фильтры, а также как зарегистрировать недавно установленные средства разбиения по словам и фильтры на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="to-view-a-list-of-languages-whose-word-breakers-are-currently-registered"></a>Просмотр списка языков, для которых установлены зарегистрированные в данный момент средства разбиения по словам  
  
1.  Используйте представление каталога [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md) следующим образом:  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### <a name="to-view-a-list-of-the-filters-that-are-currently-registered"></a>Просмотр списка зарегистрированных в данный момент фильтров  
  
1.  Используйте системную хранимую процедуру [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md) следующим образом:  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### <a name="to-register-newly-installed-word-breakers-and-filters"></a>Регистрация недавно установленных средств разбиения по словам и фильтров  
  
1.  Используйте системную хранимую процедуру [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md) для обновления списка языков следующим образом:  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### <a name="to-unregister-uninstalled-word-breakers-and-filters"></a>Отмена регистрации удаленных средств разбиения по словам и фильтров  
  
1.  Используйте **sp_fulltext_service** для обновления списка языков следующим образом:  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  Используйте **sp_fulltext_service** для перезапуска процессов узла управляющей программы фильтрации (fdhost.exe) следующим образом:  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### <a name="to-replace-existing-word-breakers-or-filters-when-installing-new-ones"></a>Замена существующих средств разбиения по словам или фильтров при установке новых  
  
1.  При подготовке к установке DLL-файла, содержащего новые средства разбиения по словам или фильтры, следует убедиться, что его имя отличается от имен существующих DLL-файлов, установленных на экземпляре сервера.  
  
2.  Скопируйте новый DLL-файл в каталог, содержащий стандартные DLL-файлы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра сервера. Расположение по умолчанию:  
  
     C:\Program Files\Microsoft SQL Server\MSSQL.*имя_экземпляра*\MSSQL\Binn  
  
    > [!IMPORTANT]  
    >  Рекомендуется загружать только подписанные и проверенные компоненты. Кроме того, службу FDHOST Launcher (MSSQLFDLauncher) рекомендуется запускать с наименьшими возможными правами доступа.  
  
3.  Установите новые средства разбиения по словам или фильтры.  
  
     **Установка и загрузка фильтров IFilter из пакета фильтров (Майкрософт)**  
  
    -   [Как зарегистрировать пакет дополнительных фильтров Microsoft IFilters в SQL Server](http://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  Загрузите вновь установленные средства разбиения по словам и фильтры на экземпляр сервера с помощью хранимой процедуры **sp_fulltext_service** следующим образом:  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  Обновите список языков с помощью хранимой процедуры **sp_fulltext_service** следующим образом:  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  Перезапустите процессы узла управляющей программы фильтрации (fdhost.exe) с помощью хранимой процедуры **sp_fulltext_service** следующим образом:  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## <a name="see-also"></a>См. также:  
 [Настройка учетной записи службы средства запуска управляющей программы полнотекстовой фильтрации](../../relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [Настройка поисковых фильтров и управление ими](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  
