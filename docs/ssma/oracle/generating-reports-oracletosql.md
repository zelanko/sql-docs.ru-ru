---
title: Создание отчетов (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Report Generation in Oracle Console, synchronize-target
- Report Generation in Oracle Console,refresh-from-database
- Report Generation in Oracle Console,write-summary-report-to
ms.assetid: ccad6262-01e1-447a-bd2b-c105154c80ce
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: ca9490b53cd55c9d8fdae5d24a045ceaf5a2e83e
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396233"
---
# <a name="generating-reports-oracletosql"></a>Создание отчетов (OracleToSQL)
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
  
    Для параметров команды для выходных отчетов (из SL. Нет. 2-4. выше) см. раздел Запуск [консоли SSMA &#40;OracleToSQL&#41;](../../ssma/oracle/executing-the-ssma-console-oracletosql.md) .  
  
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
  
**Пример**.  
  
```  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-type>"  
  
   verbose="<true/false>"  
  
   report-erors="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   assessment-report-folder="<folder-name>"  
  
   assessment-report-overwrite="<true/false>"/>  
```  
  
### <a name="synchronize-target"></a>синхронизировать — целевой объект:  
Команда **Synchronize-Target** содержит параметр **Report-Errors-to** , указывающий расположение отчета об ошибках для операции синхронизации. Затем файл с именем **таржетсинчронизатионрепорт &lt; n &gt; . XML** создается в указанном расположении, где ** &lt; n &gt; ** — уникальный номер файла, который увеличивается на цифру с каждым выполнением одной и той же команды.  
  
**Примечание.** Если указан путь к папке, параметр "Report-Errors-to" становится необязательным атрибутом для команды "Synchronize-Target".  
  
```  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="report-total-as-warning/report-each-as-warning/fail-script"  
  
   report-errors-to="<file-name/folder-name>"/>  
```  
**имя объекта:** Указывает объекты, которые учитываются при синхронизации (также могут иметь имена объектов отдельных или Group Object Name).  
  
**в случае ошибки:** Указывает, следует ли указывать ошибки синхронизации как предупреждения или ошибки. Доступные параметры для On-Error:  
  
-   отчет-всего-как-предупреждение  
  
-   отчет — каждое предупреждение  
  
-   сценарий Fail  
  
### <a name="refresh-from-database"></a>Обновление из базы данных:  
Команда **Обновить из базы данных** содержит параметр **отчет-ошибок** , указывающий расположение отчета об ошибках для операции обновления. Затем файл с именем **саурцедбрефрешрепорт &lt; n &gt; . XML** создается в указанном расположении, где ** &lt; n &gt; ** — уникальный номер файла, который увеличивается на цифру с каждым выполнением одной и той же команды.  
  
**Примечание.** Если указан путь к папке, параметр "Report-Errors-to" становится необязательным атрибутом для команды "Synchronize-Target".  
  
```  
<!-- Example: Refresh entire Schema (with all attributes)-->  
  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type ="<object-type>"  
  
   on-error="report-total-as-warning/report-each-as-warning/fail-script"  
  
   report-errors-to="<file-name/folder-name>"/>  
```  
**имя объекта:** Указывает объекты, которые считаются обновленными (они также могут иметь имена объектов отдельных или имена объектов групп).  
  
**в случае ошибки:** Указывает, следует ли указывать ошибки обновления как предупреждения или ошибки. Доступные параметры для On-Error:  
  
-   отчет-всего-как-предупреждение  
  
-   отчет — каждое предупреждение  
  
-   сценарий Fail  
  
## <a name="see-also"></a>См. также  
[Запуск консоли SSMA (Oracle)](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
