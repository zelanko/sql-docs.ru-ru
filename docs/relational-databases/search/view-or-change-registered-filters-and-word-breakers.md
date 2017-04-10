---
title: "Просмотр или изменение зарегистрированных фильтры и разделители слов | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "полнотекстовый поиск [SQL Server], средства разбиения текста на слова"
  - "полнотекстовый поиск [SQL Server], фильтры"
  - "фильтры [полнотекстовый поиск]"
  - "средства разбиения по словам [полнотекстовый поиск]"
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Просмотр или изменение зарегистрированных фильтры и разделители слов
  После того как в системе была произведена установка или удаление средств разбиения по словам или фильтров, автоматического внесения изменений на экземплярах сервера не происходит. В данном разделе описано, как можно просмотреть зарегистрированные в данный момент средства разбиения по словам и фильтры, а также как зарегистрировать недавно установленные средства разбиения по словам и фильтры на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Просмотр списка языков, для которых установлены зарегистрированные в данный момент средства разбиения по словам  
  
1.  Используйте представление каталога [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md) следующим образом:  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### Просмотр списка зарегистрированных в данный момент фильтров  
  
1.  Используйте системную хранимую процедуру [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md) следующим образом:  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### Регистрация недавно установленных средств разбиения по словам и фильтров  
  
1.  Используйте системную хранимую процедуру [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md) для обновления списка языков следующим образом:  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### Отмена регистрации удаленных средств разбиения по словам и фильтров  
  
1.  Используйте **sp_fulltext_service** для обновления списка языков следующим образом:  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  Используйте **sp_fulltext_service** для перезапуска процессов узла управляющей программы фильтрации (fdhost.exe) следующим образом:  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### Замена существующих средств разбиения по словам или фильтров при установке новых  
  
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
  
## См. также:  
 [Настройка учетной записи службы средства запуска управляющей программы полнотекстовой фильтрации](../../relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [Настройка и управление фильтрами для поиска](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  