---
title: Обновлено - документами операций SQL Studio | Документы Microsoft
description: Отображение фрагментов обновленное содержимое для последних измененных в документацию, для операций SQL Studio.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: ssops
ms.date: 04/28/2018
ms.openlocfilehash: 074ed6176480655d9d87a55eb87cbb76b3011b7e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-sql-operations-studio-docs"></a>Обновление новых и недавно: docs Studio операций SQL



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон обновлений дат:* &nbsp; **2018-02-03** &nbsp; - в - &nbsp; **2018-04-28**
- *Предметной области:* &nbsp; **операций SQL Studio**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные новые статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


- [Расширения функциональности Studio операций SQL (Предварительная версия)](extensions.md)

<!-- GeneMi:  I MANUALLY replace the ugly !INCLUDE with the name from inside the includes file. -->


&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Загрузите и установите Studio операций SQL (Предварительная версия)](#TitleNum_1)
2. [Заметки о выпуске Studio операций SQL (Предварительная версия)](#TitleNum_2)
3. [Учебник: Добавление *пять самых медленных запросов* пример мини-приложения на панель мониторинга базы данных](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-and-install-sql-operations-studio-previewdownloadmd"></a>1. &nbsp; [Загрузите и установите Studio операций SQL (Предварительная версия)](download.md)

*Обновлено: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 64.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6b4f80ad54c599e4354303a736f62e9715f99a32 18b22f464bbd8676348248ba5717b71acbab1c0d  (PR=5676  ,  Filename=download.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



   **Debian установки:**
```
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
```

   **RPM установки:**
```
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
```

   **tar.gz установки:**



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-operations-studio-preview-release-notesrelease-notesmd"></a>2. &nbsp; [Заметки о выпуске Studio операций SQL (Предварительная версия)](release-notes.md)

*Обновлено: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 20.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e2901d8a197f375f7d10ec93cbc9320362bf9278 0dde1aceceb339cb4cacd744e469f3d85d589668  (PR=5676  ,  Filename=release-notes.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**[Загрузки апреля общедоступная Предварительная версия]**


**2018 апреля (апрель общедоступную предварительную версию.)**


Дата выпуска: версия 25 апреля 2018: 0.28.6

*Общедоступной предварительной версии апреля* содержит исправления и улучшения.

- Усовершенствования для расширения предварительной версии агента SQL.
- Улучшенная поддержка больших и защищенного файла для сохранения защищенных Admin и > файлов 256 МБ в Studio операции SQL.
- Встроенная терминалов разбиения для работы с нескольких открытых терминалы за один раз.
- Число фут ограниченной установки файла на диске печать быстрее устанавливает, что время запуска.
- Продолжить исправление проблем GitHub:
   - Исправьте [выдачи 37](https://github.com/Microsoft/sqlopsstudio/issues/37): когда средства просмотра диаграмм создает ошибку, происходит непредвиденное поведение.
   - Исправить [выдачи 462](https://github.com/Microsoft/sqlopsstudio/issues/462): запрос функции: параметр для группы серверов должны быть увеличены по умолчанию.
   - Исправьте [выдачи 606](https://github.com/Microsoft/sqlopsstudio/issues/606): intellisense - неудачный вариант для команды «Обновить».
   - Исправьте [выдачи 967](https://github.com/Microsoft/sqlopsstudio/issues/967): ожидается, что план запроса при обращении XML showplan в сетке результатов.
   - Исправьте [выдачи 1023](https://github.com/Microsoft/sqlopsstudio/issues/1023): Добавление квадратных скобок для вызова ms_foreachdb из flyfishingdba.
   - Исправьте [выдачи 1048](https://github.com/Microsoft/sqlopsstudio/issues/1048): Ошибка подтверждения предварительного согласования SSL/TLS.
   - Исправьте [выдачи 1050](https://github.com/Microsoft/sqlopsstudio/issues/1050): очистить аналитики просмотреть перед отображением ошибки.
   - Исправьте [выдавать 1057](https://github.com/Microsoft/sqlopsstudio/issues/1057): восстановление и новых действий запроса в обозревателе-мини-приложения не работают.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboardtutorial-qds-sql-servermd"></a>3. &nbsp; [Учебник: Добавление *пять самых медленных запросов* пример мини-приложения на панель мониторинга базы данных](tutorial-qds-sql-server.md)

*Обновлено: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_2))

<!-- Source markdown line 94.  ms.author= "erickang".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bc128acd966898cafc04381d7d83187d28466052 a47bf93ea4165618e0e514d7900ce1461f691aae  (PR=5676  ,  Filename=tutorial-qds-sql-server.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



       },
       {
           "name": "Tasks",
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 1
           },
           "widget": {
               "tasks-widget": {}
           }
       },
       {
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 2
           },
           "widget": {
               "explorer-widget": {}
           }







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи

- [Новый + обновленные (11 + 6): &nbsp; &nbsp; **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (18 + 0): &nbsp; &nbsp; **служб Analysis Services для SQL** документы](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (218 + 14): **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (14 + 0): &nbsp; &nbsp; **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (3 + 2): &nbsp; &nbsp; **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (3 + 3): &nbsp; &nbsp; **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (7 + 10): &nbsp; &nbsp; **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (0 + 2): &nbsp; &nbsp; **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (1 + 3): &nbsp; &nbsp; **операций SQL Studio** документы](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новый + обновленные (2 + 3): &nbsp; &nbsp; **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (1 + 1): &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (5 + 2): &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (0 + 2): &nbsp; &nbsp; **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)
- [Новый + обновленные (1 + 1): &nbsp; &nbsp; **средства для SQL** документы](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи

- [Новый + обновленные (0 + 0): **Analytics Platform System для SQL** документы](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (0 + 0): **PowerShell для SQL** документы](../powershell/new-updated-powershell.md)
- [Новый + обновленные (0 + 0): **образцы для SQL** документы](../samples/new-updated-samples.md)
- [Новый + обновленные (0 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)

