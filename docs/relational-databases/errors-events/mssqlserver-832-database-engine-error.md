---
description: MSSQLSERVER_832
title: MSSQLSERVER_832
ms.custom: ''
ms.date: 08/20/2020
ms.prod: sql
ms.reviewer: ramakoni1, pijocoder, suresh-kandoth, Masha
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 832 (Database Engine error)
ms.assetid: ''
author: suresh-kandoth
ms.author: ramakoni
ms.openlocfilehash: 846ce27ff8e7d9560a6d4cc691d1523fddd913fa
ms.sourcegitcommit: ead0b8c334d487a07e41256ce5d6acafa2d23c9d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92418827"
---
# <a name="mssqlserver_832"></a>MSSQLSERVER_832
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

## <a name="details"></a>Сведения

|attribute|Значение|
|---|---|
|Название продукта|SQL Server|
|Идентификатор события|832|
|Источник события|MSSQLSERVER|
|Компонент|SQLEngine|
|Символическое имя|B_CONSTPAGECHANGED|
|Текст сообщения|Страница, которая должна была быть неизменной, изменилась (ожидаемая контрольная сумма: \<expected value>, фактическая контрольная сумма: \<actual value>, база данных \<dbid>, файл \'<filename>", страница \<pageno>). Обычно это свидетельствует о сбое памяти или другом повреждении оборудования либо ОС.|
||

## <a name="explanation"></a>Пояснение

Внешний фактор привел к изменению страницы базы данных не с помощью обычного кода ядра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемого для изменения страниц базы данных.  Возможные причины:  

- В рамках процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется поток, который некорректно выполняет запись в страницу базы данных. Такую ситуацию часто называют наложенной записью.
- Из-за проблемы с оборудованием или операционной системой произошло некорректное изменение или повреждение области памяти, в которой хранится страница базы данных.  

Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаруживает такую ситуацию, возникает ошибка 832.

## <a name="user-action"></a>Рекомендуемые действия

Чтобы найти причину ошибки, можно воспользоваться указанными ниже методами.

- Необходимо выполнить стандартные проверки оборудования или системы, чтобы определить, есть ли проблемы с памятью, ЦП или другим оборудованием. Убедитесь в том, что в системе установлены все системные драйверы, обновления операционной системы и обновления оборудования. Также рекомендуется выполнить диагностику оборудования средствами производителя, включая тесты памяти.
- Оцените, какие "внешние" библиотеки DLL, загруженные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], могут вызывать эту проблему. Сюда относятся расширенные хранимые процедуры, COM-объекты и другие библиотеки DLL, которые могут некорректно изменять память [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], зарезервированную для страниц базы данных.  

При возникновении этой ошибки следует немедленно выполнить команду `DBCC CHECKDB` применительно к базе данных, указанной в элементе \<dbid> в сообщении об ошибке.

## <a name="more-information"></a>Дополнительные сведения

Эта ошибка обнаруживается фоновой задачей, называемой LazyWriter. (Команда для этой задачи называется LAZY WRITER.) Поэтому она не возвращается клиентскому приложению. Эта ошибка регистрируется в журнале событий приложений Windows как событие с идентификатором 832.  

Проверяются только страницы, которые в настоящее время не изменены в кэше (не являются "грязными"). Именно поэтому в сообщении используется термин "неизменная": страница не изменялась с момента считывания с диска. Кроме того, страница была считана с диска как "чистая", так как она имеет значение контрольной суммы на странице и не вызвала ошибку контрольной суммы (сообщение 824). Однако страница могла быть изменена в некоторый момент времени после этой ошибки, а затем записана на диск с некорректным изменением. При возникновении этой ошибки перед записью на диск вычисляется новая контрольная сумма с учетом всех изменений. Поэтому страница может быть повреждена на диске, но последующие операции чтения с диска могут не вызывать ошибку контрольной суммы. Для любой базы данных, указанной в сообщении об этой ошибке, важно выполнить команду `DBCC CHECKDB`.  

Возможно, что даже команда `DBCC CHECKDB` не сообщит об ошибке для страницы в этом состоянии после записи на диск. Причина может быть в том, что некорректные изменения могут находиться в частях страницы, которые не содержат данных или важных сведений о структуре страницы или строк, либо могут не обнаруживаться инструкцией CHECKDB.  

Дополнительные сведения о сообщении 832 можно также получить в документе [Основные операции ввода-вывода в SQL Server, раздел 2](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).
