---
title: "Предыдущие выпуски SQL Server Management Studio | Документация Майкрософт"
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87f593c3-8b76-4c12-963a-31d35f2fb294
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 0927784589c1f7227b432ff49f81f29de20083ec
ms.openlocfilehash: 200753bf64d92043171788852227c6199b64711d
ms.contentlocale: ru-ru
ms.lasthandoff: 05/27/2017

---
# <a name="previous-sql-server-management-studio-releases"></a>Предыдущие выпуски SQL Server Management Studio
  
Доступны следующие предыдущие выпуски SQL Server Management Studio.
   
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-1653-releasehttpgomicrosoftcomfwlinklinkid840946"></a>![Загрузить](../ssdt/media/download.png) [выпуска SQL Server Management Studio 16.5.3](http://go.microsoft.com/fwlink/?LinkID=840946)

**Сведения о версии**  
  
*В этом выпуске SSMS используется изолированная оболочка Visual Studio 2015.*  
Номер выпуска: 16.5.3  
Номер сборки для этого выпуска: 13.0.16106.4

## <a name="changelog"></a>Журнал изменений  

16.5.3

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



## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-165-releasehttpgomicrosoftcomfwlinklinkid832812"></a>![Скачать](../ssdt/media/download.png) [выпуск 16.5 SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkID=832812)

**Сведения о версии**  
  
*В этом выпуске SSMS используется изолированная оболочка Visual Studio 2015.*  
Номер выпуска: 16.5  
Номер сборки этого выпуска: 13.0.16000.28

**Известные проблемы в этой сборке**  

1. Команда Invoke-Sqlcmd ошибочно вставляет несколько строк при возникновении ограничения CHECK. [Элемент Microsoft Connect: 811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

2. Версии не на английском языке не работают полностью при создании групп доступности.

3. При щелчке на плане запроса XML не открывается правильный интерфейс SSMS.

**Журнал изменений**

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


   
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-1641-september-2016-releasehttpgomicrosoftcomfwlinklinkid828615"></a>![скачать](../ssdt/media/download.png) [Выпуск SQL Server Management Studio 16.4.1 (сентябрь 2016 г.)](http://go.microsoft.com/fwlink/?LinkID=828615)

**Сведения о версии**  
  
*В этом выпуске SSMS используется изолированная оболочка Visual Studio 2015.*  
Номер выпуска: 16.4.1  
Номер сборки этого выпуска: 13.0.15900.1
  
**Известные проблемы в этой сборке**  

1. **Для входа в экземпляр SSMS с помощью универсальной проверки подлинности Active Directory можно использовать только одну учетную запись Azure Active Directory.**  
    Это ограничение распространяется только на универсальную проверку подлинности Active Directory: вы можете входить на разные серверы, используя проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.
    
    Чтобы обойти это ограничение, используйте другой экземпляр среды SSMS для входа в систему с другой учетной записью Azure Active Directory. 
    
2. **Команды платформы приложений уровня данных (DacFx) и конструктор схем в SSMS не поддерживают универсальную проверку подлинности Active Directory.**  
    Команды, использующие DacFx (например, команды импорта и экспорта) и конструктор схем в среде SSMS сейчас не поддерживают универсальную проверку подлинности Active Directory.
    
    Чтобы обойти это ограничение, используйте другие способы проверки подлинности, доступные в SSMS: проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.

3. **Решение SSMS может подключаться только к экземплярам служб SQL Server 2016 Integrated Services (SSIS 2016).**  
    Мы знаем об ограниченной совместимости служб SQL Server Integration Services, которое не дает подключаться к предыдущим версиям.
    
    Чтобы временно решить эту проблему, подключитесь к экземпляру службы SQL Server Integration Service с помощью [выпуска SSMS, который соответствует вашему экземпляру SSIS](../ssms/previous-sql-server-management-studio-releases.md). 
  
4. **SSMS не сохраняет планы обслуживания для решения SQL Server 2008 R2 и более ранних версий SQL Server.**  
    Мы надеемся устранить это ограничение в будущем. А пока вы сможете сохранять планы обслуживания с помощью выпуска [SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) .  
    
5. **Для локализованных версий SSMS может потребоваться установка дополнительного пакета безопасности.**  
При использовании локализованных версий SSMS [пакет обновления безопасности KB 2862966](https://support.microsoft.com/en-us/kb/2862966) требуется при установке на следующих платформах: Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2.
  
6. **Диспетчер конфигурации SQL Server не будет запущен, если на клиентском компьютере не установлено решение SQL Server.**  
    Если на клиентском компьютере не установлено решение SQL Server, а вы запускаете диспетчер конфигурации SQL Server, появится следующее сообщение об ошибке:   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * Если экземпляр SQL Server добавлен в список зарегистрированных серверов в среде SSMS:  
        1. Перейдите в представление "Зарегистрированные серверы" в среде SSMS.  
        2. Щелкните правой кнопкой мыши экземпляр SQL Server, который нужно настроить.  
        3. Запустите диспетчер конфигурации SQL Server из контекстного меню.    
          
      * Если экземпляр SQL Server не был добавлен в список зарегистрированных серверов в среде SSMS:  
        1. Откройте командную строку с правами администратора.  
        2. Запустите средство Mofcomp с помощью такой команды:  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Чтобы после запуска средства Mofcomp изменения вступили в силу, перезапустите службу WMI с помощью такой команды:  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  

 
**Журнал изменений** 

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
    
*  Исправлена проблема в Analysis Services PaaS, из-за которой создание скрипта на странице "Свойства" сервера приводило к появлению скрытого диалогового окна подключения.
    
*  Исправлена проблема, из-за которой нажатие клавиш CTRL+Q не открывало панель инструментов быстрого запуска.
    
*  Исправлена проблема, из-за которой изменение параметра MaxSize для базы данных в диалоговом окне "Свойства" было невозможно для баз данных размером больше 2 ТБ.  
[Элемент Microsoft Connect № 1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  Исправлена проблема, из-за которой мастер восстановления баз данных не принимал имена файлов с пробелом в начале:   
[Элемент Microsoft Connect № 2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)

*  Исправлена проблема, из-за которой мастер восстановления баз данных не принимал имена файлов с пробелом в начале:   
[Элемент Microsoft Connect № 2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-163-august-2016-releasehttpgomicrosoftcomfwlinklinkid824938"></a>![скачать](../ssdt/media/download.png) [Выпуск SQL Server Management Studio 16.3 (август 2016 г.)](http://go.microsoft.com/fwlink/?LinkID=824938)
 15 августа 2016 г. | Номер версии: 13.0.15700.28

**Функции**  
1. Новый вариант проверки подлинности — "универсальная проверка подлинности Active Directory"
2. Новые командлеты для модуля SQL Server PowerShell
3. Усовершенствования помощника по настройке ядра СУБД (DTA) и шаблоны расширенных событий
4. Бета-версия поддержки [мониторов с высоким разрешением в SSMS](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/)

[Дополнительные сведения о функциях доступны в журнале изменений SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

**Известные проблемы**

Ниже перечислены проблемы и ограничения, связанные с последним выпуском SQL Server Management Studio.  

1. **Для входа в экземпляр SSMS с помощью универсальной проверки подлинности Active Directory можно использовать только одну учетную запись Azure Active Directory.**  
    Это ограничение распространяется только на универсальную проверку подлинности Active Directory: вы можете входить на разные серверы, используя проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.
    
    Чтобы обойти это ограничение, используйте другой экземпляр среды SSMS для входа в систему с другой учетной записью Azure Active Directory. 
    
2. **Команды платформы приложений уровня данных (DacFx) и конструктор схем в SSMS не поддерживают универсальную проверку подлинности Active Directory.**  
    Команды, использующие DacFx (например, команды импорта и экспорта) и конструктор схем в среде SSMS сейчас не поддерживают универсальную проверку подлинности Active Directory.
    
    Чтобы обойти это ограничение, используйте другие способы проверки подлинности, доступные в SSMS: проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.

3. **Решение SSMS может подключаться только к экземплярам служб SQL Server 2016 Integrated Services (SSIS 2016).**  
    Мы знаем об ограниченной совместимости служб SQL Server Integration Services, которое не дает подключаться к предыдущим версиям.
    
    Чтобы временно решить эту проблему, подключитесь к экземпляру службы SQL Server Integration Service с помощью [выпуска SSMS, который соответствует вашему экземпляру SSIS](../ssms/previous-sql-server-management-studio-releases.md). 
  
4. **SSMS не сохраняет планы обслуживания для решения SQL Server 2008 R2 и более ранних версий SQL Server.**  
    Мы надеемся устранить это ограничение в будущем. А пока вы сможете сохранять планы обслуживания с помощью выпуска [SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) .  
    
5. **Для локализованных версий SSMS может потребоваться установка дополнительного пакета безопасности.**  
При использовании локализованных версий SSMS [пакет обновления безопасности KB 2862966](https://support.microsoft.com/en-us/kb/2862966) требуется при установке на следующих платформах: Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2.
  
6. **Диспетчер конфигурации SQL Server не будет запущен, если на клиентском компьютере не установлено решение SQL Server.**  
    Если на клиентском компьютере не установлено решение SQL Server, а вы запускаете диспетчер конфигурации SQL Server, появится следующее сообщение об ошибке:   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * Если экземпляр SQL Server добавлен в список зарегистрированных серверов в среде SSMS:  
        1. Перейдите в представление "Зарегистрированные серверы" в среде SSMS.  
        2. Щелкните правой кнопкой мыши экземпляр SQL Server, который нужно настроить.  
        3. Запустите диспетчер конфигурации SQL Server из контекстного меню.    
          
      * Если экземпляр SQL Server не был добавлен в список зарегистрированных серверов в среде SSMS:  
        1. Откройте командную строку с правами администратора.  
        2. Запустите средство Mofcomp с помощью такой команды:  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Чтобы после запуска средства Mofcomp изменения вступили в силу, перезапустите службу WMI с помощью такой команды:  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  


**Исправления**
1. Исправлена ошибка: теперь можно просматривать открытый текст в зашифрованных столбцах больших объектов AlwaysEncrypted в SSMS (элемент Microsoft Connect № 2413024).
2. Исправлена ошибка: теперь диалоговое окно Always Encrypted отображается без сбоя, когда стили оформления Windows (например, дисплей с высокой контрастностью) не включены.
3. Исправлена ошибка "Метод не найден", которая не позволяет подключаться к экземплярам SQL Server.
4. Исправлена ошибка, которая заключается в том, что решение SSMS дает сбой, когда выполняется создание функции секционирования со смещением даты и времени.
5. Исправлена ошибка: удалено требование Microsoft .NET 3.5 для запуска средства администрирования распределенного воспроизведения (DReplay.exe).
6. Исправлена ошибка в мастере развертывания служб Analysis Services. Благодаря этому исправлению поддерживаются полные имена сервера.
7. Исправлена ошибка: теперь в SSMS секции отображаются в табличных моделях служб Analysis Services с использованием модели совместимости версии 2016 (элемент Microsoft Connect № 2845053).

[Дополнительные сведения об исправлениях доступны в журнале изменений SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)
 
---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-july-2016-hotfix-update-releasehttpgomicrosoftcomfwlinklinkid822301"></a>![скачать](../ssdt/media/download.png) [Выпуск исправления для SQL Server Management Studio за июль 2016](http://go.microsoft.com/fwlink/?LinkID=822301)

13 июля 2016 года | Номер версии: 13.0.15600.2

**Функции**  
1. Поддержка хранилища данных Azure SQL в среде SSMS.   
2. Существенные обновления модуля SQL Server PowerShell.   
3. Значительно уменьшено время ожидания соединения с базами данных Azure SQL.  
4. Улучшена поддержка табличных баз данных SQL Server 2016 (уровень совместимости 1200) в диалоговом окне процесса служб Analysis Services.   

[Дополнительные сведения и исправления доступны в журнале изменений SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

**Известные проблемы** 
1. **Установщик для выпуска исправления для SSMS за июль отображается как выпуск для SSMS за август.**
На странице настройки этого исправления написано "Август" из-за внутреннего параметра сборки. На самом деле этот пакет представляет собой исправление для июльского выпуска SSMS. 
2. **Решению SSMS не удается подключиться к экземплярам SQL Server после установки исправления за июль 2016 года.**
Нам известно о проблеме, связанной с последним обновлением SSMS. Попытка подключиться к серверу приводит к появлению такого сообщения об ошибке: 
   ```
    "Method not found: 'Void Microsoft.SqlServer.Management.Common.SqlConnectionInfo.set_ApplicationIntent(System.String)'"
    ```
  
    Исправление этой проблемы будет доступно в следующем выпуске SSMS. Чтобы временно ее решить, вы можете удалить, а затем переустановить SSMS. Дополнительные сведения вы можете почерпнуть [в этой дискуссии Microsoft Connect по этой проблеме](https://connect.microsoft.com/SQLServer/feedback/details/2925257/not-able-to-connect-to-sql-server-instances-after-installing-ssms-2016-july-update).
    
3. **Решение SSMS дает сбой, когда происходит попытка выбрать учетную запись хранения Azure.**
Июльский выпуск SSMS и июльское исправление дают сбой, если вы пытаетесь выбрать учетную запись хранения Azure и у вас нет классической учетной записи хранения.
Исправления этой ошибки будет доступно в одном из будущих выпусков SSMS. Вот как вы можете временно решить эту проблему. Сделайте резервную копию своих баз данных или восстановите их в учетную запись хранения Azure. Для этого создайте классическую учетную запись хранения или [воспользуйтесь T-SQL](https://msdn.microsoft.com/library/jj720552(v=sql.120).aspx).

4. **SSMS отображает только классические учетные записи хранения Azure в мастерах восстановления и резервного копирования.**
Июльский выпуск SSMS и июльское исправление отображают только классические учетные записи хранения Azure при создании учетных данных, если вы пытаетесь выполнить резервное копирование или восстановление с помощью соответствующих мастеров.
Исправления этой ошибки будет доступно в одном из будущих выпусков SSMS. Вот как вы можете временно решить эту проблему. Сделайте резервную копию своих баз данных или восстановите их в доступную учетную запись хранилища Azure. Для этого создайте классическую учетную запись хранения или [воспользуйтесь T-SQL](https://msdn.microsoft.com/library/jj720552(v=sql.120).aspx). 

5. **Для локализованных версий SSMS может потребоваться установка дополнительного пакета безопасности.**
При установке на следующие платформы для использования неанглоязычных локализованных выпусков SSMS требуется [пакет обновления безопасности KB 2862966](https://support.microsoft.com/en-us/kb/2862966) : Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2.
6. **Решение SSMS может подключаться только к экземплярам служб SQL Server 2016 Integrated Services (SSIS 2016).** Мы знаем об ограниченной совместимости служб SQL Server Integration Services, которое не дает подключаться к предыдущим версиям.
Чтобы временно решить эту проблему, подключитесь к экземпляру службы SQL Server Integration Service с помощью выпуска SSMS, который соответствует вашему экземпляру SSIS.
7. **SSMS не сохраняет планы обслуживания для решения SQL Server 2008 R2 и более ранних версий SQL Server.** Мы создаем исправление для этой проблемы. А пока его нет, вы можете сохранять планы обслуживания с помощью выпуска SSMS 2014 (см. ниже).
8. **Диспетчер конфигурации SQL Server не запускается, если на клиентском компьютере не установлено решение SQL Server.** Если на клиентском компьютере не установлено решение SQL Server, а вы запускаете диспетчер конфигурации SQL Server, отображается сообщение об ошибке "Не удалось подключиться к поставщику WMI". Обходное решение.
    * Откройте командную строку с правами администратора.
    * Запустите средство Mofcomp с помощью такой команды:  
      mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"
    * Чтобы после запуска средства Mofcomp изменения вступили в силу, перезапустите службу WMI с помощью такой команды:  
       net stop "Windows Management Instrumentation"  
       net start "Windows Management Instrumentation"

**Исправления**  
1. Исправление ошибки в конструкторе запросов SSMS, позволяющее добавлять в конструктор таблицы, для которых у пользователя нет разрешений SELECT.
2. Исправление ошибки, обеспечивающее поддержку функций TRY_CAST() и TRY_CONVERT() [(элемент Microsoft Connect № 2453461)](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast)в IntelliSense.
3. Исправление ошибки в окне редактора SSMS, позволяющее перетаскивать и открывать файлы SQL [(элемент Microsoft Connect № 2690658)](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios).
4. Исправление ошибки в службах Analysis Services, обеспечивающее правильное отображение поставщика канала данных для многомерных моделей служб Analysis Services.
5. Исправление ошибки в SSMS, решающее проблему сбоя при попытке изменить ссылку на соединение в конструкторе таблиц SSMS [(элемент Microsoft Connect № 2721052)](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms).  

[Дополнительные сведения и исправления ошибок доступны в журнале изменений SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-june-2016-releasehttpgomicrosoftcomfwlinklinkid799832"></a>![скачать](../ssdt/media/download.png) [Выпуск SQL Server Management Studio за июнь 2016 года](http://go.microsoft.com/fwlink/?LinkID=799832)

1 июня 2016 года | Номер версии: 13.0.15000.23

**Функции**  
Новый упрощенный установщик SSMS. Автономные выпуски SSMS. Автоматическая проверка обновлений. Новое диалоговое окно "Быстрый поиск". Решение SSMS, собранное на основе оболочки Visual Studio 2015, и многое другое.   
[Дополнительные сведения доступны в журнале изменений SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

**Известные проблемы** 
1. **Создание сценариев PowerShell в мастере Always Encrypted сейчас не работает.**
Исправление для этой проблемы будет доступно в одном из последующих ежемесячных обновлений SSMS.
2. **Когда вы подключены к базе данных SQL Azure, пункт контекстного меню "Зашифровать столбцы" в обозревателе объектов отключен для таблиц и столбцов.** Исправление для этой проблемы будет доступно в одном из последующих ежемесячных обновлений SSMS. Временно решить проблему можно так. Чтобы зашифровать столбцы и таблицы базы данных SQL Azure, щелкните базу данных правой кнопкой мыши в обозревателе объектов, выберите "Задачи", а затем — "Зашифровать столбцы".
3. **Решение SSMS может подключаться только к экземплярам служб SQL Server 2016 Integrated Services (SSIS 2016).** Мы знаем об ограниченной совместимости служб SQL Server Integration Services, которое не дает подключаться к предыдущим версиям.
Чтобы временно решить эту проблему, подключитесь к экземпляру службы SQL Server Integration Service с помощью выпуска SSMS, который соответствует вашему экземпляру SSIS.
4. **SSMS не сохраняет планы обслуживания для решения SQL Server 2008 R2 и более ранних версий SQL Server.** Мы создаем исправление для этой проблемы. А пока его нет, вы можете сохранять планы обслуживания с помощью выпуска SSMS 2014 (см. ниже).
5. **Диспетчер конфигурации SQL Server не запускается, если на клиентском компьютере не установлено решение SQL Server.** Если на клиентском компьютере не установлено решение SQL Server, а вы запускаете диспетчер конфигурации SQL Server, отображается сообщение об ошибке "Не удалось подключиться к поставщику WMI". Обходное решение.
    * Откройте командную строку с правами администратора.
    * Запустите средство Mofcomp с помощью такой команды:  
      mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"
    * Чтобы после запуска средства Mofcomp изменения вступили в силу, перезапустите службу WMI с помощью такой команды:  
       net stop "Windows Management Instrumentation"  
       net start "Windows Management Instrumentation"

**Исправления**  
1. Диалоговое окно быстрого поиска в решении SSMS, которое лучше интегрировано в текущий документ и позволяет выполнять поиск с помощью регулярных выражений ([элемент Microsoft Connect № 2735513](https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/)).
2. Исправление ошибки в контекстной справке SSMS, вызываемой с помощью клавиши F1. Благодаря этому исправлению документы и статьи отображаются правильно.
3. Исправление ошибки в представлении "Регрессированные запросы" хранилища данных запросов, из-за которой решение SSMS дает сбой во время прокрутки.
4. Исправление ошибки в соединителе OLEDB служб Excel Analysis Services. Благодаря этому можно подключить Excel 2016 к службам SQL Server Analysis Services.
5. Исправление ошибки в диалоговом окне "Подключение" решения SSMS. Благодаря этому диалоговое окно подключения отображается на том же мониторе, что и главное окно SSMS в системах с несколькими мониторами ([элемент Microsoft Connect № 724909)](https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/).
6. Исправления ошибок, которые возникают при работе элемента Always Encrypted. Исправлена ошибка, из-за которой пункт меню Always Encrypted неправильно работал с базами данных Stretch. Исправлена также ошибка, из-за которой мастер Always Encrypted неправильно использует поставщик SafeNet (Luna SA) HSM.

---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-2014-sp1httpdownloadmicrosoftcomdownload156156992e6-f7c7-4e55-833d-249bd2348138enux86sqlmanagementstudiox86enuexe"></a>![скачать](../ssdt/media/download.png) [SQL Server Management Studio 2014 с пакетом обновления 1 (SP1)](http://download.microsoft.com/download/1/5/6/156992E6-F7C7-4E55-833D-249BD2348138/ENU/x86/SQLManagementStudio_x86_ENU.exe)

14 мая 2015 года | Номер версии 12.0.4100.1

**Функции**  
Улучшенная поддержка Базы данных SQL Azure в виде нового меню на портале управления, интеграции конструктора таблиц и многого другого.   
[Дополнительные сведения доступны в заметках о выпуске](https://support.microsoft.com/en-us/kb/3058865).

**Известные проблемы**  
Недоступно

**Исправления**
1. Если имя плана обслуживания и первое имя SUB_PLAN совпадают, решение SSMS дает сбой, когда выполняется задача "Перемещение плана обслуживания".
2. Вы не можете отладить хранимую процедуру, которая вызывает sp_executesql в SQL Server Management Studio (SSMS). Когда вы нажимаете клавишу F11, отображается сообщение об ошибке "Для экземпляра объекта не задана ссылка на объект" ([элемент Microsoft Connect № 736509](https://connect.microsoft.com/SQLServer/feedback/details/736509/sql-server-2012-rtm-management-studio-cannot-debug-sp-executesql)).
3. Решению SSMS не удается полноценно управлять полным текстом в SQL Server Express ([элемент Microsoft Connect № 740181](https://connect.microsoft.com/SQLServer/feedback/details/740181/management-studio-does-not-fully-manage-full-text-in-sql-server-express)).
4. SSMS обрабатывает нумерованные хранимые процедуры непоследовательно [(элемент Microsoft Connect № 764197](https://connect.microsoft.com/SQLServer/feedback/details/764197/ssms-2012-inconsistently-handles-numbered-procedures)).
5. Иногда решение SSMS дает сбой, когда закрывается, что приводит к его автоматическому перезапуску ([элемент Microsoft Connect № 774317](https://connect.microsoft.com/SQLServer/feedback/details/774317/sql-server-management-studio-2012-2014-crashes-when-closing)).
6. Когда вы пишете сценарии для разрешений уровня столбцов в SSMS, создание сценария ведет к дублированию инструкций ([элемент Microsoft Connect № 797967](https://connect.microsoft.com/SQLServer/feedback/details/797967/ssms-create-script-duplicates-the-statements-for-grant-or-deny-column-permissions)).
7. Решение SSMS дает сбой, когда вы пытаетесь обновить значок окна SSMS на панели задач ([элемент Microsoft Connect № 799430](https://connect.microsoft.com/SQLServer/feedback/details/799430/ssms-2012-sp-1-cu-5-installed-crash-when-enforce-refresh-on-connect)).

---
## <a name="downloadssdtmediadownloadpng-sql-server-management-studio-2012-sp3httpdownloadmicrosoftcomdownloadf67f673709c-d371-4a64-8bf9-c1dd73f60990enux86sqlmanagementstudiox86enuexe"></a>![скачать](../ssdt/media/download.png) [SQL Server Management Studio 2012 с пакетом обновления 3 (SP3)](http://download.microsoft.com/download/F/6/7/F673709C-D371-4A64-8BF9-C1DD73F60990/ENU/x86/SQLManagementStudio_x86_ENU.exe)  
  
21 ноября 2015 года | Номер версии: 11.0.6020.0

**Функции**  
Полнофункциональные экспресс-выпуски SSMS. Фрагменты кода. Индексы columnstore и многое другое.  
[Дополнительные сведения доступны в заметках о выпуске.](https://support.microsoft.com/en-us/kb/3072779)
 
**Известные проблемы**  
Недоступно

**Исправления**
1. Когда вы импортируете данные с помощью мастера экспорта и импорта, отсутствующие столбцы невозможно указать в сообщении об ошибке.
2. Когда вы восстанавливаете разностную резервную копию в SSMS, появляется сообщение об ошибке "Не удается создать план восстановления из-за нарушения непрерывности цепочки LSN".

---
## <a name="additional-downloads"></a>Дополнительные скачиваемые файлы  
Список всех загрузок для SQL Server Management Studio см. в [центре загрузки Майкрософт](https://www.microsoft.com/en-us/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
Чтобы получить последнюю версию среды SQL Server Management Studio, перейдите на страницу [Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).  

---  
## <a name="related-resources"></a>Связанные ресурсы
[Update Center for Microsoft SQL Server (Центр обновлений для Microsoft SQL Server)](https://technet.microsoft.com/sqlserver/ff803383.aspx)   
[Учебник. Среда SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[Форум SQL Server Management Studio](https://social.msdn.microsoft.com/forums/en-us/home?forum=sqltools)  

  

