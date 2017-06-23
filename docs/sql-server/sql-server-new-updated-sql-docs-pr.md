---
title: "Обновлено - документации SQL Server | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 05/23/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 7fba3b05943b93c0a2c0e76c2d0d5f2696a48d1c
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---
# <a name="new-and-recently-updated-sql-server-docs"></a>Обновление новых и недавно: документы по SQL Server



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон обновлений дат:* &nbsp; **2017 г-05-01** &nbsp; - в - &nbsp; **2017 г-05-23**
- *Предметной области:* &nbsp; **SQL Server**.




&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе отображается отрывки обновлений, полученные из статей, в которых были недавно крупных обновлений.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2017-release-notessql-server-2017-release-notesmd"></a>1. &nbsp;[Заметки о выпуске SQL Server 2017 г.](sql-server-2017-release-notes.md)

*Updated: 2017-05-17* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 28.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 84e7a2a49f2893d49380db1ad75695d9a4fd59b2 27a145ad30c10fd667f926d2e092b88c0ba586c5 -->



**2017 г. SQL Server CTP 2.1 (май 2017 г.)**

**Документация (CTP-версия 2.1)**

- **Проблема и последствия для клиентов:** документации для [! ВКЛЮЧИТЬ [ssSQLv14_md--... ограничена /includes/sssqlv14-MD.md]), а содержимое входит в состав [! ВКЛЮЧИТЬ [ssSQL15_md--... набор документации /includes/sssql15-MD.md]).  Содержимого в статьях, специфичные для [! ВКЛЮЧИТЬ [ssSQLv14_md--... /includes/sssqlv14-MD.MD)] будет помещен вместе с **применяется к**. 
- **Проблема и последствия для клиентов:** не автономного содержимого доступен для [! ВКЛЮЧИТЬ [ssSQL14_md--... набор документации /includes/sssql14-MD.md]).

**SQL Server Reporting Services (CTP-версия 2.1)**


- **Проблема и последствия для клиентов:** при наличии служб SQL Server Reporting Services и Power BI сервера отчетов на том же компьютере и удалить один из них, больше не можно соединиться с сервером отчетов в оставшихся с диспетчером конфигурации сервера отчетов.
- **Инструкции по решению** Чтобы обойти эту проблему, необходимо выполнить следующие операции после удаления одного из серверов.

    1. Откройте командную строку с правами администратора.
    2. Перейдите в каталог, где оставшиеся сервер отчетов установлен.

        *Расположение по умолчанию для сервера отчетов Power BI: C:\Program Files\Microsoft Power BI отчета сервера*

        *Расположение по умолчанию для SQL Server Reporting Services: C:\Program Files\Microsoft SQL Server Reporting Services*

    3. Затем перейдите к следующей папке. Это будет *SSRS* или *PBIRS* в зависимости от того, что остается.
    4. Перейдите в папку WMI.
    5. Выполните следующую команду:

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        Если вы видите его следующей ошибки можно игнорировать.

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

**TSqlLanguageService.msi (CTP-версия 2.1)**


- **Проблема и последствия для клиентов:** после установки на компьютере с версии 2016 *TSqlLanguageService.msi* (либо через программу установки SQL или установлены как автономный распространяемый пакет) версии v13.* (SQL 2016) *Microsoft.SqlServer.Management.SqlParser.dll* и *Microsoft.SqlServer.Management.SystemMetadataProvider.dll* удаляются. Все приложения, которые имеют зависимость от версии 2016 этих сборок затем прекращает работать, предоставляя сообщение об ошибке: *ошибка: не удалось загрузить файл или сборку ' Microsoft.SqlServer.Management.SqlParser, версия = 13.0.0.0, язык и региональные параметры = neutral, PublicKeyToken = 89845dcd8080cc91 "или одну из ее зависимостей. Системе не удается найти указанный файл.*




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-what39s-new-in-sql-server-2017what-s-new-in-sql-server-2017md"></a>2. &nbsp;[Что &#39; новые возможности SQL Server 2017 г.](what-s-new-in-sql-server-2017.md)

*Updated: 2017-05-22* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1))

<!-- Source markdown line 31.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b3e965f62414af06d42f88497958a4bca67befce 82ad09ae9a917f26db3e2210b5cf89585e0e4c4e -->



**Новые возможности SQL Server 2017 г CTP 2.1 (май 2017 г.)**

** SQL Server Database Engine **

- Новый DMF [sys.dm_db_log_stats--... / relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md), представленные для предоставления атрибутов на уровне сводки и сведения о файлах журнала транзакций; удобно использовать для наблюдения за работоспособностью журнала транзакций.  
- Эта CTP-версия содержит исправления и улучшения производительности для компонента Database Engine.
- Чтобы получить подробный список 2017 г CTP усовершенствования в предыдущих выпусках CTP-версии. в разделе [новые возможности в 2017 г. SQL Server (компонент Database Engine)--... / database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

**SQL Server Reporting Services (SSRS)**

- SQL Server Reporting Services больше не доступно для установки программой установки SQL Server, начиная с CTP-версии 2.1.
- Комментарии, теперь доступны для отчетов. Комментарии позволяют добавить перспективу для возможности отчета и совместной работы с другими пользователями в вашей организации. Можно также включить вложения в комментарий.
- Для более подробные SSRS возможности новой информации, включая сведения из предыдущих версий см. в разделе [новые возможности в Reporting Services —... / reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 
- Сведения о сервере отчетов Power BI см. в разделе [приступить к работе с сервером отчетов Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).

**Изучение служб машины SQL Server**

- Нет новых компонентов службы обучения машины в этой CTP-версии.
- Более подробные служб обучения машины возможности новой информации, включая данные из предыдущей CTP-версии см. в разделе [новые возможности в SQL Server машины обучения службы--... / advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).  

**SQL Server Analysis Services (SSAS)**

- В этой CTP-версии нет новых функций SSAS.  
- Дополнительные сведения об улучшениях и исправления ошибок в этом выпуске см. в разделе [новые возможности в SQL Server 2017 г Analysis Services —... / analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).  





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

Compact представлены ссылки на обновленные статьи, перечисленные в предыдущем разделе.

1. [Заметки о выпуске SQL Server 2017 г.](#TitleNum_1)
2. [Какой &#39; новые возможности SQL Server 2017 г.](#TitleNum_2)


<a name="sisters2"/>

&nbsp;

## <a name="sister-articles"></a>Филиалы статей

В этом разделе перечислены схожий статей для недавно обновлены статьи в других предметных областей, в одном репозитории GitHub.


&nbsp;

[Microsoft и**sql документы pr** ](https://github.com/microsoftdocs/sql-docs-pr/) репозитория в GitHub.com:

- [Недавно обновлены: **реляционных баз данных и Microsoft SQL Server** документы](/sql/relational-databases/relational-databases-new-updated-sql-docs-pr)
- [Недавно обновлены: **Microsoft SQL Server** документы](/sql/sql-server/sql-server-new-updated-sql-docs-pr)
- [Недавно обновлены: **Transact-SQL в SQL Server** документы](/sql/t-sql/t-sql-new-updated-sql-docs-pr)


&nbsp;

<!--
[Microsoft/**azure-docs**](https://github.com/microsoft/azure-docs/) repository on GitHub.com:

- [Sisters list for **azure-docs** repo](https://docs.microsoft.com/azure/sql-server-new-updated-azure-docs/#sisters2)
-->

&nbsp;



