---
title: "Среда SQL Server Management Studio (SSMS) — журнал изменений | Документация Майкрософт"
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
caps.latest.revision: 72
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2144751277bb10897e0ed39ee24dbad8a32b4ce
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Changelog (SSMS)

## <a name="ssms-1653-release"></a>Выпуск SSMS 16.5.3
Общедоступная версия | Номер сборки: 13.0.16106.4

В этом выпуске были решены следующие проблемы.

* Устранена проблема, появившаяся в SSMS 16.5.2. Эта проблема приводила к раскрытию узла "Таблица", если в таблице было несколько разреженных столбцов.

* Пользователи могут развертывать пакеты SSIS, содержащие диспетчер подключений OData, который используется для подключения ресурса Microsoft Dynamics AX или CRM Online к каталогу SSIS. Дополнительные сведения см. в разделе [Диспетчер соединений OData](https://msdn.microsoft.com/library/dn584133.aspx).

* Настройка Always Encrypted для существующей таблицы завершается с ошибками, в которых указаны посторонние объекты. [Идентификатор Connect 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* Настройка Always Encrypted для существующей базы данных с несколькими схемами не работает. [Идентификатор Connect 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* Мастер зашифрованного столбца в Always Encrypted завершается с ошибкой из-за того, что база данных содержит представления, ссылающиеся на системные представления. [Идентификатор Connect 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* При шифровании с помощью Always Encrypted ошибки из-за обновления модулей после шифрования обрабатываются неправильно.

* В меню *Открыть последние* не отображаются недавно сохраненные файлы. [Идентификатор Connect 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS замедляет работу при щелчке таблицы правой кнопкой мыши (при работе через удаленное подключение в Интернете). [Идентификатор Connect 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)
 
* Устранена проблема с полосой прокрутки конструктора SQL. [Идентификатор Connect 3114856](http://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Контекстное меню таблиц ненадолго зависает. 
 
* SSMS иногда выдает исключения в мониторе активности и завершает работу с ошибкой. [Идентификатор Connect 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* SSMS 2016 аварийно завершает работу с ошибкой "Процесс был завершен из-за внутренней ошибки в среде выполнения .NET: IP 71AF8579 (71AE0000), код выхода 80131506"


## <a name="ssms-1651-release"></a>Выпуск SSMS 16.5.1
Общедоступен | Номер сборки: 13.0.16100.1

* Исправлена проблема, при которой Invoke-Sqlcmd ошибочно вставляет несколько строк при возникновении ограничения CHECK. [Элемент Microsoft Connect: 811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

* Исправлена проблема, при которой версии не на английском языке не работали полностью при создании групп доступности.

* Исправлена проблема, когда при щелчке плана запроса XML не открывался правильный пользовательский интерфейс SSMS.


## <a name="ssms-165-release"></a>Выпуск SSMS 16.5
Общедоступен | Номер сборки: 13.0.16000.28

* Исправлена проблема, связанная со сбоем, который мог происходить при щелчке базы данных с именем таблицы, содержащим ";:".
* Исправлена проблема, из-за которой изменения, внесенные на странице "Модель" в окне свойств табличной базы данных AS, становятся причиной вывода исходного определения при помощи скрипта. 
[Элемент Microsoft Connect № 3080744](https://connect.microsoft.com/SQLServer/feedback/details/3080744) 
* Исправлена проблема с добавлением временных файлов в список "Последние файлы".  
[Элемент Microsoft Connect № 2558789](https://connect.microsoft.com/SQLServer/feedback/details/2558789)
* Исправлена проблема с отключением элемента меню "Управление сжатием" для узлов пользовательской таблицы в дереве обозревателя объектов.  
[Элемент Microsoft Connect № 3104616](https://connect.microsoft.com/SQLServer/feedback/details/3104616)

* Исправлена проблема, при которой пользователь не может задать размер шрифта для обозревателя объектов, обозревателя зарегистрированных серверов, обозревателя шаблонов, а также для данных обозревателя объектов. Для обозревателей будет использоваться шрифт среды разработки.  
[Элемент Microsoft Connect № 691432](https://connect.microsoft.com/SQLServer/feedback/details/691432)

* Исправлена проблема, при которой SSMS всегда повторно подключается к базе данных по умолчанию при потере соединения.  
[Элемент Microsoft Connect № 3102337](https://connect.microsoft.com/SQLServer/feedback/details/3102337)

* Исправлены многие проблемы, связанные с высоким разрешением в окне управления политиками и редактора запросов, включая значки плана выполнения.

* Исправлена проблема, из-за которой невозможно настраивать шрифты и цвета для расширенных событий.

* Исправлена проблема, связанная со сбоями SSMS, происходившими при закрытии приложения или при попытке отобразить диалоговое окно ошибки.


## <a name="ssms-1641-september-2016-release"></a>Выпуск SSMS 16.4.1 (сентябрь 2016 г.)
Общедоступен | Номер сборки: 13.0.15900.1

*  Устранена проблема со сбоем инструкции ALTER и изменением хранимой процедуры:  
[Элемент Microsoft Connect № 3103831](https://connect.microsoft.com/SQLServer/feedback/details/3103831)

* Новые командлеты "Read-SqlTableData", "Read-SqlViewData" и "Write-SqlTableData" для просмотра и записи данных с помощью PowerShell.  
[Карта Trello Read-SqlTableData](https://trello.com/c/FXVUNJ8x/131-read-sqltabledata)  
[Элемент Microsoft Connect № 2685363](https://connect.microsoft.com/SQLServer/feedback/details/2685363)
    
* Новый командлет "Add-SqlLogin" для новых сценариев управления входом с помощью PowerShell.  
[Элемент Microsoft Connect № 2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952)
    
*  Улучшена поддержка и удобство использования для пользователей, подключающихся к разным национальным облакам.
    
    
*  Исправлена проблема, из-за которой возникают исключения "Недостаточно памяти".  
[Элемент Microsoft Connect № 3062914](https://connect.microsoft.com/SQLServer/feedback/details/3062914)  
[Элемент Microsoft Connect № 3074856](https://connect.microsoft.com/SQLServer/feedback/details/3074856)
    
*  Исправлена проблема, из-за которой сортировка по схеме была недоступна.  
[Элемент Microsoft Connect № 3058105](https://connect.microsoft.com/SQLServer/feedback/details/3058105)  
[Элемент Microsoft Connect № 3101136](https://connect.microsoft.com/SQLServer/feedback/details/3101136)
    
*  Исправлена проблема, из-за которой окно "Мониторинг" для растянутой базы данных было недоступно.
    
*  Исправлена проблема, из-за которой окно справки F1 всегда открывало веб-контент. Пользователи теперь могут выбрать справку из Интернета или автономную справку в разделе "Задать параметры справки" в меню "Справка".   
[Элемент Microsoft Connect № 2826366](https://connect.microsoft.com/SQLServer/feedback/details/2826366)
    
*  Исправлена проблема, из-за которой при создании скрипта для табличной модели служб Analysis Services уровня 1200 не извлекался пароль для создания скриптов, даже если в версии сервера он извлекался (объект клиентской модели теперь синхронизируется перед созданием скриптов).
    
*  Исправлена проблема, из-за которой параметр "SELECT TOP N ROWS" создавал устаревший синтаксис для оператора TOP.  
[Элемент Microsoft Connect № 3065435](https://connect.microsoft.com/SQLServer/feedback/details/3065435)
    
*  Исправлены разные проблемы с макетом в SSMS, в том числе на странице "Свойства входа" и в дополнительных параметрах выполнения запросов.   
[Элемент Microsoft Connect № 3058199](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Элемент Microsoft Connect № 3079122](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Элемент Microsoft Connect № 3071384](https://connect.microsoft.com/SQLServer/feedback/details/3071384)
    
*  Исправлена проблема, из-за которой решение создавалось автоматически каждый раз, когда пользователь открывал новое окно запроса.   
[Элемент Microsoft Connect № 2924667](https://connect.microsoft.com/SQLServer/feedback/details/2924667)    
[Элемент Microsoft Connect № 2917742](https://connect.microsoft.com/SQLServer/feedback/details/2917742)   
[Элемент Microsoft Connect № 2612635](https://connect.microsoft.com/SQLServer/feedback/details/2612635)
    
*  Исправлена проблема, из-за которой временные таблицы было невозможно раскрыть в обозревателе объектов в системных базах данных.  
[Элемент Microsoft Connect № 2551649](https://connect.microsoft.com/SQLServer/feedback/details/2551649)
    
*  Исправлена проблема, из-за которой среда SSMS запускала запрос SELECT @@trancount после выполнения пакетной операции.    
[Элемент Microsoft Connect № 3042364](https://connect.microsoft.com/SQLServer/feedback/details/3042364)
    
*  Исправлена проблема в Analysis Services, из-за которой создание скрипта на странице "Свойства" сервера приводило к появлению скрытого диалогового окна подключения.
    
*  Исправлена проблема, из-за которой нажатие клавиш CTRL+Q не открывало панель инструментов быстрого запуска.
    
*  Исправлена проблема, из-за которой изменение параметра MaxSize для базы данных в диалоговом окне "Свойства" было невозможно для баз данных размером больше 2 ТБ.  
[Элемент Microsoft Connect № 1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  Исправлена проблема, из-за которой мастер восстановления баз данных не принимал имена файлов с пробелом в начале:   
[Элемент Microsoft Connect № 2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



## <a name="ssms-163-august-2016-release"></a>Выпуск SSMS 16.3 (август 2016)
Общедоступная версия | Номер версии: 13.0.15700.28

* Теперь каждому ежемесячному выпуску SSMS присваивается номер.

* [Новый вариант аутентификации — **универсальная аутентификация Active Directory**](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/). Это механизм аутентификации на основе маркеров, работающий с помощью Azure Active Directory. Он поддерживает многофакторную и встроенную аутентификацию, а также проверку пароля.

* Новые шаблоны расширенных событий, соответствующие шаблонам SQL Server Profiler [(элемент Microsoft Connect № 2543925)](https://connect.microsoft.com/SQLServer/feedback/details/2543925/sql-server-extended-events-profiler-tool). См. дополнительные сведения о включенных в выпуск [шаблонах SQL Server Profiler](https://msdn.microsoft.com/library/ms190176.aspx).

* Новые диалоговые окна "Создание базы данных" и "Свойства базы данных" для баз данных Azure SQL.

* Новые командлеты Get-SqlLogin и Remove-SqlLogin, которые помогают управлять входом в SQL Server с помощью PowerShell.  
*Связанные запросы об ошибках от клиентов*   
[Элемент Microsoft Connect № 2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952/)

* Новый командлет PowerShell New-SqlColumnMasterKeySettings, который помогает создавать главные ключи столбцов для произвольных поставщиков и путей к ключам.

* Новое диалоговое окно "Создание базы данных", которое упрощает создание баз данных SQL Azure в SSMS.

* Поддержка фильтрации в узле "Базы данных" обозревателя объектов SSMS. Перейдите к узлу "Базы данных" в обозревателе объектов и щелкните значок фильтра на панели инструментов обозревателя, чтобы отфильтровать список баз данных.

* Поддержка учетных записей хранения, относящихся к типу Azure-Resource Manager (ARM), в мастерах резервного копирования и восстановления.

* [Исходная бета-поддержка для мониторов с высоким разрешением](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/).  
*Связанные запросы об ошибках от клиентов*   
[элемент Microsoft Connect № 1129301](https://connect.microsoft.com/SQLServer/feedback/details/1129301/management-studio-is-unusable-on-a-4k-display), [элемент Microsoft Connect № 1858763](https://connect.microsoft.com/SQLServer/feedback/details/1858763/), [элемент Microsoft Connect № 1852671](https://connect.microsoft.com/SQLServer/feedback/details/1852671/), [элемент Microsoft Connect № 1487643](https://connect.microsoft.com/SQLServer/feedback/details/1487643/),  [элемент Microsoft Connect № 1355641](https://connect.microsoft.com/SQLServer/feedback/details/1355641/), [элемент Microsoft Connect № 2161595](https://connect.microsoft.com/SQLServer/feedback/details/2161595/), [элемент Microsoft Connect № 1854041](https://connect.microsoft.com/SQLServer/feedback/details/1854041/), [элемент Microsoft Connect № 1055617](https://connect.microsoft.com/SQLServer/feedback/details/1055617/), [элемент Microsoft Connect № 2448774](https://connect.microsoft.com/SQLServer/feedback/details/2448774/), [элемент Microsoft Connect № 1521405](https://connect.microsoft.com/SQLServer/feedback/details/1521405/), [элемент Microsoft Connect № 2117853](https://connect.microsoft.com/SQLServer/feedback/details/2117853/), [элемент Microsoft Connect № 2014256](https://connect.microsoft.com/SQLServer/feedback/details/2014256/), [элемент Microsoft Connect № 2162218](https://connect.microsoft.com/SQLServer/feedback/details/2162218/), [элемент Microsoft Connect № 2344551](https://connect.microsoft.com/SQLServer/feedback/details/2344551/), [элемент Microsoft Connect № 1664436](https://connect.microsoft.com/SQLServer/feedback/details/1664436/), [элемент Microsoft Connect № 2554043](https://connect.microsoft.com/SQLServer/feedback/details/2554043/), [элемент Microsoft Connect № 2983216](https://connect.microsoft.com/SQLServer/feedback/details/2983216/), [элемент Microsoft Connect № 2021706](https://connect.microsoft.com/SQLServer/feedback/details/2021706/)

* Внесены улучшения в помощник по настройке ядра СУБД. Теперь он поддерживает автоматическое чтение рабочих нагрузок из хранилища запросов SQL Server.

* Внесены улучшения в помощник по настройке ядра СУБД. Теперь он отображает рекомендации для кластеризованных индексов columnstore, некластеризованных индексов columnstore и индексов rowstore.

* Теперь команды консоли базы данных можно отправлять с помощью командлетов PowerShell служб SQL Server Analysis Services.

* Исправление ошибки, которое позволяет просматривать открытый текст в зашифрованных столбцах больших объектов AlwaysEncrypted в SSMS.  
*Связанные запросы об ошибках от клиентов*   
[Элемент Microsoft Connect № 2413024](https://connect.microsoft.com/SQLServer/feedback/details/2413024/cannot-view-cleartext-of-alwaysencrypted-lob-columns-in-ssms)

* Исправление ошибки в диалоговом окне Always Encrypted, из-за которой происходит сбой, когда стили оформления Windows не включены (например, включение дисплея с высокой контрастностью).

* Исправлена ошибка "Метод не найден", которая не позволяет подключаться к экземплярам SQL Server.

* Исправлена ошибка, которая заключается в том, что решение SSMS дает сбой, когда выполняется создание функции секционирования со смещением даты и времени.

* Исправление ошибки, которое добавляет удаленное требование Microsoft .NET 3.5 для запуска средства администрирования распределенного воспроизведения (DReplay.exe).

* Исправлена ошибка в мастере развертывания служб Analysis Services. Благодаря этому исправлению поддерживаются полные имена сервера.

* Исправление ошибки в SSMS, благодаря которому отображаются секции в табличных моделях служб Analysis Services, использующих модель совместимости 2016.  
*Связанные запросы об ошибках от клиентов*   
[Элемент Microsoft Connect № 2845053](https://connect.microsoft.com/SQLServer/feedback/details/2845053/ssms-cannot-display-partitions-in-tabular-models-in-2016-compatibility-level) 

* Повышена производительность и исправлены ошибки в табличных моделях служб Analysis Services и общих управляющих объектах SQL Server (SMO). 


---
## <a name="ssms-july-2016-hotfix-update-release"></a>Исправление SSMS за июль 2016 года 
Общедоступная версия | Номер версии: 13.0.15600.2

* **Исправление ошибки в среде SSMS, которое делает доступными отсутствующие пункты контекстного меню**.  
*Связанные запросы об ошибках от клиентов*  
[Элемент Microsoft Connect № 2883440](https://connect.microsoft.com/SQLServer/feedback/details/2883440/lost-table-design-and-edit-top-n-rows-in-tables-context-menu)  
[Элемент Microsoft Connect № 2909644](https://connect.microsoft.com/SQLServer/feedback/details/2909644/ssms-2016-is-missing-edit-options-against-sql-express-2014)  
[Элемент Microsoft Connect № 2924345](https://connect.microsoft.com/SQLServer/feedback/details/2924345/some-ssms-object-explorer-right-click-menu-options-missing-in-july-update)

---
## <a name="ssms-july-2016-release"></a>Выпуск SSMS за июль 2016 года 
Общедоступная версия | Номер версии: 13.0.15500.91

* *Изменение от 5 июля:* **улучшена поддержка табличных баз данных SQL Server 2016 (уровень совместимости 1200) в диалоговом окне процесса и в мастере развертывания служб Analysis Services.**

* *Изменение от 5 июля:* **добавлен параметр XACT_ABORT в диалоговом окне "Параметры выполнения запроса" SSMS. В этом выпуске он по умолчанию включен и при возникновении ошибки в среде выполнения сообщает SQL Server о необходимости выполнить откат всей операции и отменить пакет.**

* **Поддержка хранилища данных Azure SQL в среде SSMS.**

* **Существенные обновления модуля SQL Server PowerShell. Сюда входит новый [модуль SQL PowerShell и новые командлеты для постоянного шифрования, агента SQL Server и журналов ошибок SQL](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update)**.

* **Поддержка создания сценариев PowerShell в мастере постоянного шифрования**.

* **Значительно уменьшено время ожидания соединения с базами данных Azure SQL.**

* **Добавлено диалоговое окно "Резервное копирование по URL-адресу", позволяющее создавать учетные данные хранилища Azure для резервных копий SQL Server 2016. Это упрощает процесс сохранения резервных копий хранилищ в учетной записи хранилища Azure.**
 
* **Добавлено диалоговое окно "Восстановление", оптимизирующее восстановление резервной копии базы данных SQL Server 2016 из службы хранилища Microsoft Azure.**
 
* **Исправление ошибки в конструкторе запросов SSMS, позволяющее добавлять в конструктор таблицы, для которых у пользователя нет разрешений SELECT.**

* **Исправление ошибки, обеспечивающее поддержку функций TRY_CAST() и TRY_CONVERT() в IntelliSense.**  
*Связанные запросы об ошибках от клиентов*  
[элемент Microsoft Connect № 2453461](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast).

* **Исправление ошибки в модуле PowerShell, позволяющее загружать расширение SQLAS служб Analysis Services.**  
*Связанные запросы об ошибках от клиентов*  
[элемент Microsoft Connect № 2544902](https://connect.microsoft.com/SQLServer/feedback/details/2544902/ssms-march-2016-refresh-sqlps-failed-to-load-the-sqlas-extension).

* **Исправление ошибки в окне редактора SSMS, позволяющее перетаскивать и открывать файлы SQL.**  
*Связанные запросы об ошибках от клиентов*  
[элемент Microsoft Connect № 2690658](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios).

* **Исправление ошибки в приложении Profiler, решающее проблему сбоя при выходе из приложения.**  
*Связанные запросы об ошибках от клиентов*  
[элемент Microsoft Connect № 2616550](https://connect.microsoft.com/SQLServer/feedback/details/2616550/sql-server-2016-rc2-profiler-version-13-0-1300-275-wont-close-after-trace-is-started-even-after-trace-is-stopped).  
[элемент Microsoft Connect № 2319968](https://connect.microsoft.com/SQLServer/Feedback/Details/2319968).

* **Исправление ошибки в SSMS, решающее проблему сбоя, которая возникает при попытке изменить ссылку на соединение в конструкторе таблиц SSMS.**  
*Связанные запросы об ошибках от клиентов*  
[элемент Microsoft Connect № 2721052](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms).

* **Исправление ошибки в SSMS, позволяющее генерировать сценарии базы данных для членов роли db_owner.**  
*Связанные запросы об ошибках от клиентов*  
[элемент Microsoft Connect № 2869241](https://connect.microsoft.com/SQLServer/feedback/details/2869241/error-with-script-database-as-create-to-in-ssms-2008r2-and-ssms-2016-june).

* **Исправление ошибки в редакторе SSMS, решающее проблему задержки при закрытии вкладки запроса в случае, если сервер отключается от сети.**  
*Связанные запросы об ошибках от клиентов*  
[элемент Microsoft Connect № 2656058](https://connect.microsoft.com/SQLServer/feedback/details/2656058/ssms-2014-2016-query-tab-takes-significantly-longer-to-close-if-the-instance-it-was-connected-to-is-now-offline).

* **Исправление ошибки, позволяющее включать параметр резервного копирования в базах данных SQL Server Express.**  
*Связанные запросы об ошибках от клиентов*  
[элемент Microsoft Connect № 2801910](https://connect.microsoft.com/SQLServer/feedback/details/2801910/ssms-2016-backup-option-not-appearing-in-tasks);  
[элемент Microsoft Connect № 2874434](https://connect.microsoft.com/SQLServer/feedback/details/2874434/backup-missing-from-tasks-context-menu-in-ssms-2016-when-you-are-connected-to-an-express-instance).

* **Исправление ошибки в службах Analysis Services, обеспечивающее правильное отображение поставщика канала данных для многомерных моделей служб Analysis Services.**

----
## <a name="ssms-june-2016-generally-available-release"></a>Общедоступный выпуск SSMS за июнь 2016 года
Общедоступная версия | Номер версии: 13.0.15000.23

* **В 2016 году решение SSMS становится общедоступным с июньского выпуска.**

* **Диалоговое окно быстрого поиска в решении SSMS, которое лучше интегрировано в текущем документе и позволяет выполнять поиск с помощью регулярных выражений.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/>

* **Улучшения в установщике SSMS позволяют отслеживать ход выполнения установки и обрабатывать коды выхода для автоматической установки через сценарии.**

* **Исправление ошибки в контекстной справке SSMS, вызываемой с помощью клавиши F1. Благодаря этому исправлению документы и статьи отображаются правильно.**

* **Исправление ошибки в представлении "Регрессированные запросы" хранилища данных запросов, из-за которой решение SSMS дает сбой во время прокрутки.** 

* **Исправление ошибки в соединителе OLEDB служб Excel Analysis Services. Благодаря этому можно подключить Excel 2016 к службам SQL Server Analysis Services.**

* **Исправление ошибки в диалоговом окне "Подключение" решения SSMS. Благодаря этому в системах с несколькими мониторами диалоговое окно подключения отображается на том же мониторе, что и главное окно SSMS.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/>
<https://connect.microsoft.com/SQLServer/feedback/details/755689/sql-server-management-studio-connect-to-server-popup-dialog/>  
<https://connect.microsoft.com/SQLServer/feedback/details/389165/sql-server-management-studio-gets-confused-dealing-with-multiple-displays/>

* **Исправления ошибок, которые возникают при работе элемента Always Encrypted. Исправлена ошибка, из-за которой пункт меню Always Encrypted неправильно работал с базами данных Stretch. Кроме того, исправлена ошибка, из-за которой мастер Always Encrypted неправильно использует поставщик SafeNet (Luna SA) HSM.**

---
## <a name="ssms-april-2016-preview"></a>Предварительная версия SSMS за апрель 2016 
Номер версии: 13.0.14000.36
  
* **Улучшение в установщике SSMS, которое добавляет понятные для пользователей сообщения об ошибках.**  
  
* **Улучшения в мастере базы данных Stretch, которое добавляет поддержку для предикатов**.  
  
* **Улучшения в командлете AlwaysEncrypted Powershell, которое добавляет интерфейсы API шифрования ключей**.  
  
* **Исправление ошибки, которое отключает компонент IntelliSense на панели инструментов SSMS, если он отключен в диалоговом окне "Сервис, Параметры".**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2555163/sql-2016-rc2-turning-off-intellisense-from-options-does-not-turn-it-off-on-toolbar/>  
    
* **Улучшения и исправления ошибок в пользовательском интерфейсе сравнения элементов Showplan: сокращен интервал, используемый длительными планами запросов**.  
  
* **Исправления ошибок в SSMS, из-за которых решение SSMS дает сбой, когда закрывается**.   
  
* **Исправления ошибок в мастере Always Encrypted. Они позволяют сохранять разрешения пользователей во время шифрования и выполнять операции отсоединения базы данных после завершения работы мастера**.  
  
* **Исправление в диалоговом окне "Новый главный ключ столбца". Это исправление предоставляет отчет о попытке создать ключ с помощью поставщика неподдерживаемого алгоритма шифрования.**  
  
---  
## <a name="ssms-march-2016-preview-refresh"></a>Обновление предварительной версии SSMS за март 2016 года
Номер версии: 13.0.13000.55
  
* **Решение SSMS теперь использует изолированную оболочку Visual Studio 2015.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2390544/update-ssms-to-use-visual-studio-2015-dependencies/>  
  
* **Новая панель быстрого запуска позволяет быстро находить элементы и параметры меню. (Изолированная оболочка VS 2015)**  
  
* **Улучшения в параметрах темы SSMS, которые добавляют поддержку светлой темы SSMS. (Изолированная оболочка VS 2015)**  
  
* **Исправление ошибки в параметре меню "Сервис" решения SSMS. Это исправление правильно сбрасывает ярлыки запросов, если нажать кнопку "Восстановить значения по умолчанию".**  
  
* **Исправление ошибки в новых шаблонах проекта SSMS, которое отображает читаемые имена шаблонов.**  
  
* **Разрешена ошибка, возникавшая при просмотре журнала заданий агента SQL Server в SSMS.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2458860/error-viewing-job-history-microsoft-datawarehouse-sqm/>  
    
* **Исправление ошибки, которое позволяет выполнять автономную установку SSMS, то есть установку без подключения к Интернету. (Изолированная оболочка VS 2015)**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2497178/cannot-install-ssms-when-server-has-no-internet-access/>  
    
* **Исправление ошибки, которое позволяет сохранить текущий каталог пользователя при импорте модуля SQL Server PowerShell (SQLPS).**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2434605/loading-sqlps-module-changes-current-directory-to-ps-sqlserver/>  
    
* **Исправление ошибки в модуле SQL Server PowerShell (SQLPS), которое позволяет использовать утвержденные команды PowerShell.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2432891/sqlps-module-uses-unapproved-powershell-verbs/>  
    
* **Исправление ошибки в модуле SQL Server PowerShell (SQLPS), которое позволяет загружать его быстрее.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2429153/sqlps-module-is-slow-to-load/>  
    
* **Исправление ошибки в шагах заданий агента SQL Server, которое позволяет изменять шаги задания.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2453996/issues-with-agent-in-ssms-2016-rc0-13-0-12000-65/>  
    
* **Исправление ошибки в обозревателе объектов SSMS, которое позволяет отображать таблицы в алфавитном порядке.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2424718/sql-server-2016-ssms-table-list-confusing/>  
    
* **Исправление ошибки в раскрывающемся меню "доступные базы данных". Это исправление позволяет отображать правильный список имен баз данных, когда подключение к решению SQL Server изменяется.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2513420/available-databases-drop-down-box-does-not-update-when-connection-changes-in-ssms/>  
    
* **Исправление ошибки в сочетаниях клавиш SSMS, которое позволяет нажатием клавиш CTRL+U переносить фокус на раскрывающееся меню "доступные базы данных".**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2534820/ssms-ctrl-u-doesnt-work/>  
  
---  
## <a name="ssms-march-2016-preview"></a>Предварительная версия SSMS за март 2016 года 
Номер версии: 13.0.12500.29 
  
* **Улучшения веб-установщика SSMS, которые позволяют выполнять навигацию с помощью сочетаний клавиш.**  
  
* **Улучшение мастера AlwaysEncrypted, которое поддерживает шифрование псевдонимов типов данных.**  
  
* **Исправление ошибки в мастере новых групп доступности AlwaysOn. Это исправление позволяет отображать правильное максимальное количество целей автоматической отработки отказа.**  
*Связанные запросы об ошибках от клиентов* <https://connect.microsoft.com/SQLServer/feedback/details/2333670/ssms-is-showing-the-wrong-number-of-maximum-automatic-failover-targets/>  
    
* **Исправление ошибок в веб-установщике SSMS, которое исправляет ошибки, мешающие установке.**  
*Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2181548/sql-server-2016-ctp-3-2-management-studio-setup/>  
    
* **Исправление ошибки в выпуске предварительной версии SSMS, которое позволяет сохранять планы обслуживания SQL Server 2012 и более ранних версий.**  
      
* **Исправления ошибок в мастере резервного копирования. Эти исправления позволяют использовать несколько настраиваемых имен для чередующихся резервных копий и отображать соответствующее имя файла резервного копирования, если после выбора учетных данных хранилища введено новое имя.**  
  
---  
## <a name="ssms-february-2016-preview"></a>Предварительная версия SSMS за февраль 2016 года 
Номер версии: 13.0.12000.65
  
* **Улучшение монитора активности, благодаря которому отображаются текстовые параметры, когда в решении SSMS включены настройки высокой контрастности.**  
  
* **Улучшение диалогового окна мастера Always Encrypted, благодаря которому отображается предупреждение, если параметры сортировки столбца изменяются во время шифрования.**  
  
* **Улучшение в управлении политикой, которое поддерживает создание условий в ключах шифрования столбца, значениях ключей шифрования столбцов и главных ключах столбца.**  
  
* **Исправление ошибки, которое повышает удобство использования диалогового окна очистки главного ключа Always Encrypted и сообщений об ошибках Always Encrypted.**  
  
* **Исправление ошибки, которое отключает смену главного ключа столбца Always Encrypted, если существует только один ключ.**  
  
* **Исправление ошибки "инициализатор типа", которая возникает, если диалоговое окно Always Encrypted открыто с помощью январского выпуска SSMS или выпуска SSMS, который объединен в один пакет с SQL Server RC0.**  
  
---  
## <a name="ssms-january-2016-preview"></a>Предварительная версия SSMS за январь 2016 года 
Номер версии: 13.0.11000.78 
  
* **Исправление ошибки в SSMS, позволяющее удалять сеансы расширенных событий (XEvent).**  
  
* **Исправление ошибки, позволяющее открыть диалоговое окно свойств для группы доступности SQL Server 2014.**  
 *Связанные запросы об ошибках от клиентов*  
 <https://connect.microsoft.com/SQLServer/feedback/details/1609719/>  
     
* **Исправление ошибки, позволяющее добавлять реплики Azure в группы доступности.**  
 *Связанные запросы об ошибках от клиентов*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2029135/>  
     
* **Исправление ошибки, позволяющее открывать диалоговое окно свойств для баз данных SQL Server 2014.**  
 *Связанные запросы об ошибках от клиентов*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2080209/>  
     
* **Исправление ошибки, позволяющее удалять повторяющиеся столбцы, которые отображаются для каждой таблицы, подключенной к базе данных SQL Azure.**  
 *Связанные запросы об ошибках от клиентов*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2103116/>  
---  
## <a name="ssms-december-2015-preview"></a>Предварительная версия среды SSMS за декабрь 2015 года 
Номер версии: 13.0.900.73
  
* **Улучшения в сравнении Showplan позволяют сравнить текущий план выполнения запроса с планом, сохраненным в файле.**  
  
* **Улучшенная поддержка IntelliSense для встроенных индексов columnstore в среде SSMS.**  
  
* **Исправление ошибки мастера сеансов расширенных событий, позволяющее выбирать шаблоны при подключении к серверу Azure версии 12.**  
  
* **Новые позиции табуляции в диалоговых окнах "Создать аудит" и "Создать имя входа" в папке "Безопасность", упрощающие навигацию с помощью клавиатуры.**  
  
* **Исправление ошибки для включения возможности "Переключиться на вкладку результатов после выполнения запроса", если в среде SSMS настроено отображение результатов в виде сетки.**   
 *Связанные запросы об ошибках от клиентов*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1390296/switch-to-results-tab-after-query-execution-grid-mode-in-ssms-2016>  
  
* **Исправление ошибки для отображения заголовков столбцов без усечения, если в среде SSMS настроено отображение результатов в виде сетки.**  
 *Связанные запросы об ошибках от клиентов*  
  <https://connect.microsoft.com/SQLServer/feedback/details/2004111/bugbash-column-headers-in-grid-mode-truncated-with-courier-new-8>  
      
* **Исправления для правильной установки веб-установщика SSMS.**  
 *Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/2003865/ssms-october-preview-incoherent-error-message>  
<https://connect.microsoft.com/SQLServer/feedback/details/2079557/unable-to-instal-sql-server-update-13-0-800-111-over-13-0-700-242-error-code-2711>  
  
---  
## <a name="ssms-november-2015-preview"></a>Предварительная версия SSMS за ноябрь 2015 года
Номер версии: 13.0.800.111
  
* **Поддержка масштабирования растрового изображения на дисплеях с высоким разрешением в среде SSMS.**  
  
* **Усовершенствования пользовательского интерфейса диалоговых окон и мастеров AlwaysEncrypted, упрощающие создание ключей шифрования баз данных.**  
  
* **Новый пункт контекстного меню в списке "Процессы" в мониторе активности для отображения статистики динамических запросов.**  
  
* **Исправление ошибки, включающее правильное удаление предварительных выпусков SSMS на клиентских компьютерах.**  
  *Связанные запросы об ошибках от клиентов*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1868474/ssms-2016-preview-can-be-installed-but-not-uninstalled>  
  
* **Исправление ошибки, позволяющее редактировать шаги задания в агенте заданий SQL Server даже при отсутствии файла**.  
  *Связанные запросы об ошибках от клиентов*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1769778/management-studio-2016-sql-job-agent>  
    <https://connect.microsoft.com/SQLServer/feedback/details/1502100/ssms-preview-error>  
      
* **Исправление ошибки в пункте меню "Просмотр целевых данных" для сеанса расширенных событий в базе данных, запущенной на виртуальной машине Azure.**  
  *Связанные запросы об ошибках от клиентов*:  
  <https://connect.microsoft.com/SQLServer/feedback/details/1769778/management-studio-2016-sql-job-agent>  
***  

## <a name="ssms-october-2015-preview"></a>Предварительная версия SSMS за октябрь 2015 
Номер версии: 13.0.700.242  
* **Новый модернизированный и упрощенный веб-установщик, который упрощает процесс скачивания и установки SSMS.**  
  
* **Новый мастер шифрования столбцов с постоянным шифрованием, который обеспечивает шифрование и расшифровку выбранных столбцов на стороне клиента.**  
  
* **Новое диалоговое окно смены главного ключа столбцов (CMK), которое служит для защиты баз данных с постоянным шифрованием, упрощая процесс смены ключей шифрования для обеспечения безопасности данных.**  
  
* **Новый монитор базы данных Stretch, который позволяет диагностировать и отслеживать состояние миграции данных в облако Azure.**  
  
* **Усовершенствования мастера базы данных Stretch для поддержки выбора сервера Microsoft Azure, который не находится в подписке Microsoft Azure по умолчанию.**  
  *Связанные запросы об ошибках от клиентов*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1687063/cannot-choose-from-multiple-microsoft-azure-subscriptions>  
* **Исправление ошибки, обеспечивающее правильное отображение динамического плана выполнения в SSMS.**  
  *Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/1774446/viewing-live-execution-plan-from-activity-monitor-crashes-ssms>    
* **Исправление ошибки, удаляющее недопустимые параметры сценариев SSMS моментальных снимков базы данных.**  
  *Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/1515168/ssms-scripting-of-database-snapshots-includes-invalid-options>  
* **Исправление ошибки в пользовательском интерфейсе хранилища данных запросов, отображающее сведения на панели "Основные запросы, потребляющие ресурсы".**  
  *Связанные запросы об ошибках от клиентов*  
<https://connect.microsoft.com/SQLServer/feedback/details/1737185/sql-server-2016-overall-resource-consumption-query-store-pane-issue>  
***  

## <a name="ssms-september-2015-preview"></a>Предварительная версия SSMS за сентябрь 2015 года 
Номер версии: 13.0.600.65  
* **Новое диалоговое окно правила брандмауэра, которое упрощает процесс подключения к базе данных SQL Azure.**      
    
* **Обновленное диалоговое окно "Новый индекс", разрешающее создание некластеризованных индексов rowstore, даже если есть кластеризованный индекс columnstore. Эта функция доступна для SQL 2016 и более поздних версий.**      
  *Связанные запросы об ошибках от клиентов:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1552617/creation-of-nc-index-when-clustered-columnstore-index>  
      
* **Исправление ошибки, позволяющее просмотреть и изменить шаги задания агента SQL в предварительных выпусках SSMS, выполняющихся в Windows 7.**      
  *Связанные запросы об ошибках от клиентов*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1548140/cannot-view-or-edit-any-sql-agent-job-step>,    
  <https://connect.microsoft.com/SQLServer/feedback/details/1626895/unable-to-load-dll-dts>,    
  <https://connect.microsoft.com/SQLServer/feedback/details/1576662/error-creating-new-job-step>     
      
* **Исправление ошибки, отображающее узлы активации в SSMS для SQL Server 2014 и более поздних версиях.**      
  *Связанные запросы об ошибках от клиентов*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1617533/trigger-node-missing>   
      
* **Исправления ошибок в пользовательском интерфейсе стандартного отчета о базе данных и сервере для исключения сведений о версии из заголовка.**      
  *Связанные запросы об ошибках от клиентов*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1387471/report-headings-wrongly-named>  
      
* **Исправление ошибки для предотвращения отображения узла статистики динамических запросов как полного, если он не полон.**      
  *Связанные запросы об ошибках от клиентов*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1589096/live-query-statistics-node-shows-as-completed>  
  
***      
## <a name="ssms-august-2015-preview"></a>Предварительная версия SSMS за август 2015 года 
Номер версии: 13.0.500.53
  
* **Обновления обозревателя объектов для сокращения задержки загрузки при наличии большого числа баз данных.**  
  
* **Усовершенствования для установки SSMS на компьютерах с Windows 10.**  
  
* **Исправления ошибок и обновления диспетчера конфигурации SQL Server, а также пользовательского интерфейса отчетов пользователей SSMS.**    
***  
  
## <a name="ssms-july-2015-preview"></a>Предварительная версия SSMS за июль 2015 года
Номер версии: 13.0.400.91
  
* **Схемы базы данных SQL Azure (V12).**  
  
* **Улучшенная поддержка IntelliSense для нового синтаксиса темпоральных таблиц.**  
  
* **Обновленная библиотека DacFx для поддержки последних функций баз данных SQL Azure, в том числе безопасности уровня строки и проверки подлинности Azure Active Directory.**  
  
* **Исправление ошибок (обновленный пользовательский интерфейс "проверка обновлений", исправление пользовательского интерфейса в списке "уровень совместимости" и многое другое).**  
***  
  
## <a name="ssms-june-2015-preview"></a>Предварительная версия SSMS за июнь 2015 года 
Номер версии: 13.0.300.44
  
* **Новый упрощенный веб-установщик SSMS.**  
  
* **Автоматическая проверка обновлений.**  
  
* **SSMS теперь включает поддержку полнотекстового поиска для базы данных SQL Azure (V12).**  
  
* **Реализованы наиболее распространенные запросы клиентов:**  
  * запрос "Изменить топ 200 строк" включен для таблиц и представлений в обозревателе объектов;  
  * конструктор таблиц включен для базы данных SQL Azure (V12);  
  * диалоговые окна свойств баз данных и таблиц включены для базы данных SQL Azure (V12).  
    
 * **Новый параметр для пропуска подсказки для сохранения файлов T-SQL.**  
   
 * **Поддержка мастера импорта и экспорта для новых уровней служб базы данных SQL Azure (базовый, стандартный, премиум).**  
   
 * **Прочие исправления ошибок (сценарии использования сценариев, отслеживание изменений в базах данных SQL и многое другое).**   
     
  
  
  
  
  
  
    

