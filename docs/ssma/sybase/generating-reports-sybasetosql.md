---
description: Создание отчетов (SybaseToSQL)
title: Создание отчетов (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,generating reports
- Sybase Console,refresh-from-database report
- Sybase Console,synchronize-target report
ms.assetid: 19278f6a-6d58-4867-9d71-c6228040466e
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: ff4e618126d9bb720d5bd4e8323e333c421f74f9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88372180"
---
# <a name="generating-reports-sybasetosql"></a>Создание отчетов (SybaseToSQL)
Отчеты о определенных действиях, выполняемых с помощью команд, создаются в консоли SSMA на уровне дерева объектов.  
  
Для создания отчетов используйте следующую процедуру.  
  
1.  Укажите параметр **Write-Summary-Report-to** . Связанный отчет сохраняется в виде имени файла (если указано) или в указанной папке. Имя файла является встроенным, как упоминалось в таблице ниже, где ** &lt; n &gt; ** — уникальный номер файла, который увеличивается на цифру при каждом выполнении одной и той же команды.  
  
    Команды Reports обратитесь-продажам-обратитесь:  
  
    |SL. Нет.|Get-Help|Заголовок отчета|  
    |-|-|-|  
    |1|Создание-Оценка-отчет|Ассессментрепорт &lt; n &gt; . КОД|  
    |2|Convert-Schema|Счемаконверсионрепорт &lt; n &gt; . КОД|  
    |3|Миграция данных|Датамигратионрепорт &lt; n &gt; . КОД|  
    |4|Convert-SQL-оператор|Конвертсклрепорт &lt; n &gt; . КОД|  
    |5|синхронизировать — целевой объект|Таржетсинчронизатионрепорт &lt; n &gt; . КОД|  
    |6|Обновление из базы данных|Саурцедбрефрешрепорт &lt; n &gt; . КОД|  
  
    > [!IMPORTANT]  
    > Выходной отчет отличается от отчета об оценке. Первое — это отчет о производительности выполненной команды, а второй — отчет в формате XML для программного использования.  
  
    Для параметров команды для выходных отчетов (из SL. Нет. 2-4. выше) см. раздел Запуск [консоли SSMA &#40;SybaseToSQL&#41;](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) .  
  
2.  Укажите степень детализации в выходном отчете, используя параметры детализации отчета:  
  
    |SL. Нет.|Команда и параметр|Описание вывода|  
    |-|-|-|  
    |1|verbose = "false"|Формирует сводный отчет о действии.|  
    |2|verbose = "true"|Формирует сводный и подробный отчет о состоянии для каждого действия.|  
  
    > [!NOTE]  
    > Параметры детализации отчета, указанные выше, применимы для команд Generate-Оценка-Report, Convert-Schema, remigrate-Data и Convert-SQL-инструкции.  
  
3.  Укажите степень детализации в отчетах об ошибках с помощью параметров отчетов об ошибках:  
  
    |SL. Нет.|Команда и параметр|Описание вывода|  
    |-|-|-|  
    |1|Report-Errors = "false"|Нет сведений об ошибках/предупреждениях/информационных сообщениях.|  
    |2|Report-Errors = "true"|Подробные сообщения об ошибках/предупреждения/сведения.|  
  
    > [!NOTE]  
    > Указанные выше параметры отчетов об ошибках применимы для команд Generate-Оценка-Report, Convert-Schema, remigrate-Data и Convert-SQL-инструкции.  
  
```xml  
<generate-assessment-report  
  
    object-name="<object-name>"  
  
    object-type="<object-type>"  
  
    verbose="<true/false>"  
  
    report-erors="<true/false>"  
  
    write-summary-report-to="<file-name/folder-name>"  
  
    assessment-report-folder="<folder-name>"  
  
    assessment-report-overwrite="<true/false>"  
  
/>  
```  
  
### <a name="synchronize-target"></a>синхронизировать — целевой объект:  
Команда **Synchronize-Target** содержит параметр **Report-Errors-to** , указывающий расположение отчета об ошибках для операции синхронизации. Затем файл с именем **таржетсинчронизатионрепорт &lt; n &gt; . XML** создается в указанном расположении, где ** &lt; n &gt; ** — уникальный номер файла, который увеличивается на цифру с каждым выполнением одной и той же команды.  
  
**Примечание.** Если указан путь к папке, параметр "Report-Errors-to" становится необязательным атрибутом для команды "Synchronize-Target".  
  
```xml  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
    object-name="<object-name>"  
  
    on-error="<object-type>"  
  
    report-errors-to="<file-name/folder-name>"  
  
/>  
```  
**имя объекта:** Указывает объекты, которые учитываются при синхронизации (также могут иметь имена объектов отдельных или Group Object Name).  
  
**в случае ошибки:** Указывает, следует ли указывать ошибки синхронизации как предупреждения или ошибки. Доступные параметры для On-Error:  
  
-   отчет-всего-как-предупреждение  
  
-   отчет — каждое предупреждение  
  
-   сценарий Fail  
  
### <a name="refresh-from-database"></a>Обновление из базы данных:  
Команда **Обновить из базы данных** содержит параметр **отчет-ошибок** , указывающий расположение отчета об ошибках для операции обновления. Затем файл с именем **саурцедбрефрешрепорт &lt; n &gt; . XML** создается в указанном расположении, где ** &lt; n &gt; ** — уникальный номер файла, который увеличивается на цифру с каждым выполнением одной и той же команды.  
  
**Примечание.** Если указан путь к папке, параметр "Report-Errors-to" становится необязательным атрибутом для команды "Synchronize-Target".  
  
```xml  
<!-- Example: Refresh entire Schema (with all attributes)-->  
  
<refresh-from-database  
  
    object-name="<object-name>"  
  
    object-type ="<object-type>"  
  
    on-error="report-total-as-warning/report-each-as-warning/fail-script"  
  
    report-errors-to="<file-name/folder-name> "  
  
/>  
```  
**имя объекта:** Указывает объекты, которые считаются обновленными (они также могут иметь имена объектов отдельных или имена объектов групп).  
  
**в случае ошибки:** Указывает, следует ли указывать ошибки обновления как предупреждения или ошибки. Доступные параметры для On-Error:  
  
-   отчет-всего-как-предупреждение  
  
-   отчет — каждое предупреждение  
  
-   сценарий Fail  
  
## <a name="see-also"></a>См. также:  
[Запуск консоли SSMA (Sybase)](https://msdn.microsoft.com/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
