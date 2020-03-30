---
title: Ошибка MSSQLSERVER 823 | mssqlserver_823
description: Описание и некоторые распространенные решения для ошибки Microsoft SQL Server 823 (mssqlserver_823), которая является серьезной ошибкой системного уровня. Она может нарушить целостность базы данных и должна быть устранена немедленно.
ms.custom: ''
ms.date: 01/27/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f79710c168f87f1156f6bbce780f8fd154ea1dd0
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "77013109"
---
# <a name="mssqlserver-error-823"></a>Ошибка MSSQLSERVER 823
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|823|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|B_HARDERR|  
|Текст сообщения|Операционная система возвратила ошибку %ls в SQL Server при %S_MSG в смещении %#016I64x файла «%ls». Дополнительные сведения см. в журнале ошибок SQL Server и журнале системных событий. Это серьезная ошибка системного уровня, которая угрожает целостности базы данных, поэтому она должна быть немедленно исправлена. Выполните полную проверку базы данных на согласованность (DBCC CHECKD). Эта ошибка может быть вызвана многими причинами. Дополнительные сведения см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
SQL Server использует интерфейсы API Windows (например, [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile), [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile), [ReadFileScatter](/windows/win32/api/fileapi/nf-fileapi-readfilescatter), [WriteFileGather](/windows/win32/api/fileapi/nf-fileapi-writefilegather)) для операций файлового ввода-вывода. После выполнения этих операций ввода-вывода SQL Server проверяет наличие ошибок, связанных с вызовами этих API. Если при вызове API происходит сбой из-за ошибки операционной системы, SQL Server сообщает об ошибке 823.

 В нем содержится следующая информация.
 - Файл базы данных, для которого была выполнена операция ввода-вывода.
 - Смещение в файле, где была предпринята попытка выполнить операцию ввода-вывода. Это смещение физического байта от начала файла. Деление этого числа на 8192 приводит к возвращению номера логической страницы, на которую повлияет ошибка.
 - Является ли операция ввода-вывода запросом на чтение или запись.
 - Код ошибки операционной системы и описание ошибки в круглых скобках.
 

**Ошибка операционной системы:** вызов API Windows для чтения или записи не выполнен, и SQL Server обнаруживает ошибку операционной системы, связанную с вызовом API Windows. В следующем примере показано сообщение об ошибке 823:

```
Error: 823, Severity: 24, State: 2.
2010-03-06 22:41:19.55 spid58 The operating system returned error 1117 (The request could not be performed because of an I/O device error.) to SQL Server during a read at offset 0x0000002d460000 in file 'e:\program files\Microsoft SQL Server\mssql\data\mydb.MDF'. Additional messages in the SQL Server error log and system event log may provide more detail. This is a severe, system-level error condition that threatens database integrity and must be corrected immediately. It is recommended to complete a full database consistency check (DBCC CHECKDB). This error can be caused by many factors; for more information, see SQL Server Books Online.
```

Ошибки инструкции DBCC CHECKDB в базе данных, связанной с файлом, могут быть не указаны в сообщении об ошибке. Вы можете выполнить инструкцию DBCC CHECKDB, если появилась ошибка 823. Если инструкция DBCC CHECKDB не сообщает о каких-либо ошибках, возможно, возникла временная неполадка системы или проблема с диском.

Дополнительные диагностические сведения для ошибок 823 могут быть записаны в файл журнала ошибок SQL Server при использовании флага трассировки 818.
Дополнительные сведения см. в статье [KB 826433: добавлены дополнительные средства диагностики SQL Server для выявления незамеченных проблем ввода-вывода](https://support.microsoft.com/help/826433/sql-server-diagnostics-added-to-detect-unreported-i-o-problems-due-to).


## <a name="cause"></a>Причина
Сообщение об ошибке 823 обычно указывает на наличие проблемы с базовой системой хранения данных, оборудованием или драйвером в пути запроса ввода-вывода. Эта ошибка может возникать, если в файловой системе возникли несоответствия или если файл базы данных поврежден. В случае чтения файла SQL Server будет четыре раза повторять запрос на чтение, прежде чем вернет ошибку 823. Если повторная операция завершается успешно, запрос не завершится ошибкой, но в журнал ошибок и журнал событий будет записано сообщение [825](mssqlserver-825-database-engine-error.md).

## <a name="user-action"></a>Действие пользователя  
 - Проверьте таблицу [suspect_pages](../system-tables/suspect-pages-transact-sql.md) в MSDB на наличие других страниц, которые сталкиваются с этой проблемой (в той же или другой базе данных).
 - Проверьте согласованность баз данных, расположенных на том же томе (что и в сообщении 823), с помощью команды DBCC CHECKDB. Если при выполнении команды DBCC CHECKDB обнаружены несоответствия, используйте инструкции из раздела [Устранение ошибок согласованности базы данных, обнаруженных командой DBCC CHECKB](https://support.microsoft.com/help/2015748/how-to-troubleshoot-database-consistency-errors-reported-by-dbcc-check). 
 - Проверьте журналы событий Windows на наличие ошибок или сообщений от операционной системы, устройства хранения или драйвера устройства. Если они связаны с этой ошибкой, сначала устраните эти ошибки. Например, помимо сообщения 823, можно также увидеть событие вроде "Драйвер обнаружил ошибку контроллера в \Device\Harddisk4\DR4", о которой сообщает дисковый источник в журнале событий. В этом случае необходимо проверить наличие этого файла на устройстве, а затем сначала исправить ошибки диска.
 - Используйте служебную программу [SQLIOSim](https://support.microsoft.com/help/231619/how-to-use-the-sqliosim-utility-to-simulate-sql-server-activity-on-a-d), чтобы узнать, можно ли воспроизвести ошибки 823 за пределами обычных запросов ввода-вывода SQL Server. Служебная программа SQLIOSim поставляется с SQL Server 2008 и более поздними версиями, поэтому нет необходимости в отдельном скачивании. Обычно ее можно найти в папке `C:\Program Files\Microsoft SQL Server\MSSQLxx.MSSQLSERVER\MSSQL\Binn`.
 - Обратитесь к поставщику оборудования или изготовителю устройства, чтобы убедиться, что:
   - аппаратные устройства и конфигурация соответствуют требованиям к вводу-выводу SQL Server;
   - драйверы устройств и другие программные компоненты, поддерживающие все устройства в пути ввода-вывода, обновлены.
 - Если поставщик оборудования или производитель устройства предоставил вам диагностические служебные программы, используйте их для проверки работоспособности системы ввода-вывода.
 - Проверьте, нет ли [драйверов фильтров](https://support.microsoft.com/help/2454053/use-of-system-filter-drivers-can-lead-to-sql-server-database-engine-pe), которые находятся в пути этих запросов ввода-вывода и вызывают проблемы.
   - Проверьте наличие обновлений для этих драйверов фильтра.
   - Можно ли удалить или отключить эти драйверы фильтра, чтобы определить, не исчезает ли проблема, связанная с ошибкой 823.  
