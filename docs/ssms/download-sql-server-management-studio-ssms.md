---
title: "Загрузка SQL Server Management Studio (SSMS) | Документация Майкрософт"
ms.custom: 
ms.date: 04/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "установить SSMS, скачать SSMS, последняя версия SSMS"
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- "sql management studio установка"
- "скачать sql management studio"
- "ms sql management studio"
- "установить sql management studio"
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
caps.latest.revision: 145
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cc827737cec19c11d2102f968dc2b8bc638bda86
ms.lasthandoff: 04/11/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>Скачивание SQL Server Management Studio (SSMS)
SQL Server Management Studio (SSMS) — это интегрированная среда для доступа, настройки, администрирования и разработки всех компонентов SQL Server, а также управления ими. Среда SSMS сочетает в себе обширный набор графических инструментов с рядом отличных редакторов скриптов, обеспечивая разработчикам и администраторам любой квалификации доступ к SQL Server. В этом выпуске представлена улучшенная совместимость с предыдущими версиями SQL Server, отдельный веб-установщик и всплывающие уведомления в SSMS, сообщающие о выходе новых выпусков.  

    
| ![скачиваемого файла](../ssdt/media/download.png) Скачивание SQL Server Management Studio (SSMS)  |  |
|:---|:---|
|**[Скачать SQL Server Management Studio (16.5.3)](https://go.microsoft.com/fwlink/?LinkID=840946)**|Текущий выпуск для использования в рабочей среде.|
|**[Скачать релиз-кандидат SQL Server Management Studio (17.0 RC3)](../ssms/sql-server-management-studio-ssms-release-candidate.md)**|Включает поддержку SQL Server vNext CTP1.3 и работает параллельно с версией 16.x. Не рекомендуется для использования в рабочей среде.| 


> [!NOTE]
> Теперь каждому выпуску SSMS присваивается номер (не по месяцам). SSMS распространяется бесплатно! Лицензия для установки и использования не требуется.  


## <a name="sql-server-management-studio"></a>Среда SQL Server Management Studio   
**Сведения о версии**  
  
Номер выпуска: 16.5.3  
Номер сборки для этого выпуска: 13.0.16106.4
  
**Поддерживаемые версии SQL Server**  
  
* Эта версия SSMS работает со всеми [поддерживаемыми версиями SQL Server (SQL Server 2008 — SQL Server 2016)](https://support.microsoft.com/en-us/lifecycle?C2=1044) и предоставляет высочайший уровень поддержки для работы с новейшими облачными функциями в базе данных SQL Azure и хранилище данных SQL Azure.  
* SQL Server 2000 или SQL Server 2005 напрямую не блокируются, однако некоторые функции могут работать неправильно.  
* Кроме того, один выпуск SSMS 16.x или SSMS 2016 можно установить параллельно с предыдущими версиями SSMS 2014 и более ранними версиями. 
  
**Поддерживаемые операционные системы**  
  
При использовании последнего пакета обновления этот выпуск SSMS поддерживает следующие платформы:   
 Windows 10, Windows 8, Windows 8.1, Windows 7 (SP1), Windows Server 2012 (64-разрядная), Windows Server 2012 R2 (64-разрядная), Windows Server 2008 R2 (64-разрядная)  
   
 **Доступные языки**  
> [!NOTE]  
> При установке на следующие платформы для использования неанглоязычных локализованных выпусков SSMS требуется [пакет обновления безопасности KB 2862966](https://support.microsoft.com/en-us/kb/2862966) : Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2. 
  
 Этот выпуск SSMS можно установить на следующих языках.  
[Китайский (КНР)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804) | [Китайский (Тайвань)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404) | [Английский (США)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409) | [Французский](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c)  
[Немецкий](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407) | [Итальянский](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410) | [Японский](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411) | [Корейский](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412) | [Португальский (Бразилия)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416) | [Русский](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419) | [Испанский](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)  

 
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





Полный список возможностей см. в статье   
                [Среда SQL Server Management Studio (SSMS) — журнал изменений](../ssms/sql-server-management-studio-changelog-ssms.md)  
  
Ознакомиться со списком известных проблем и способами их обхода можно в статье   
                [Заметки о выпуске SQL Server Management Studio](../ssms/sql-server-management-studio-release-notes.md)  
  
Дополнительные сведения о сборе данных об использовании см. в разделе   
                [Заявление о конфиденциальности SQL Server](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx).  
  
## <a name="previous-releases"></a>Предыдущие выпуски  
[Предыдущие выпуски SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  
  
## <a name="feedback"></a>Отзывы  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [форум клиентских средств SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Опубликуйте информацию о проблеме или предложение на Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>См. также  
[Руководство: SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[Документация по SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(v=sql.130).aspx)  
[Microsoft SQL Server](https://msdn.microsoft.com/library/bb545450.aspx)  
[Дополнительные обновления и пакеты обновления](https://technet.microsoft.com/sqlserver/ff803383.aspx)  
[Скачать SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)  



