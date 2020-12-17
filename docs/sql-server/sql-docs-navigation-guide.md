---
title: Советі по навигации в документации SQL Server
description: В руководстве и советах по навигации в технической документации SQL Server объясняются такие элементы, как главная страница, оглавление, заголовок, а также использование адресной строки и фильтра версий.
ms.date: 08/12/2020
ms.prod: sql
ms.technology: release-landing
ms.reviewer: ''
ms.custom: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || >= sql-server-linux-2017'
ms.openlocfilehash: 98fd46528437cd9a82ec7d47539db230b8be8eb8
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97409400"
---
# <a name="sql-server-docs-navigation-guide"></a>Руководство по навигации в документации по SQL Server

В этом разделе приводятся некоторые советы и рекомендации по навигации в технической документации по SQL Server.  

## <a name="hub-page"></a>Главная страница

Главная страница документации по SQL Server находится по адресу [https://aka.ms/sqldocs](https://aka.ms/sqldocs) и является точкой входа для поиска соответствующего содержимого по SQL Server.

Вы всегда можете вернуться на эту страницу, выбрав пункт **Документация по SQL** в заголовке в верхней части каждой страницы набора технической документации по SQL Server: 

![Пункт "Документация по SQL" в заголовке](media/sql-server-docs-navigation-guide/sql-docs-in-header.png)

## <a name="offline-documentation"></a>Документация в автономном режиме

Если вам требуется просматривать документацию по SQL Server в системе, не подключенной к сети, это можно сделать двумя способами. Можно создать PDF-файл нужного раздела технической документации по SQL Server или скачать автономное содержимое с помощью [автономного средства просмотра справки SQL Server](sql-server-help-installation.md). 

Если вы хотите создать PDF-файл, щелкните ссылку **Скачать в формате PDF**, которая находится в нижней части каждого оглавления.


![Скачать в формате PDF](media/sql-server-docs-navigation-guide/download-pdf.png)

## <a name="toc-symbols"></a>Символы в оглавлении 

Если в конце пункта оглавления есть значок `>`, это означает, что вы перейдете к технической документации с другим оглавлением. 

![Одинарный значок в оглавлении](media/sql-server-docs-navigation-guide/single-carrots-in-sql-docs-toc.png)

Если в конце пункта оглавления есть значок `>>`, это означает, что при переходе вы покинете сайт docs.microsoft.com. 

![Маркеры навигации по оглавлению](media/sql-server-docs-navigation-guide/double-carrots-in-sql-docs-toc.png)

Если вы перейдете на одну из этих страниц, то можете вернуться на главную страницу и в оглавление технической документации по SQL Server, выбрав пункт "Вас приветствует SQL Server >", который находится вверху каждого оглавления. 

![Возвращение в оглавление документации по SQL](media/sql-server-docs-navigation-guide/navigate-back-to-sql-toc.png)

## <a name="toc-search"></a>Поиск в оглавлении 
На сайте docs.microsoft.com можно вести поиск по оглавлению с помощью поля фильтра поиска в верхней части страницы: 

![Использование поля фильтра](media/sql-server-docs-navigation-guide/sql-docs-toc-filter.gif)

## <a name="version-filter"></a>Фильтр версий
В технической документации по SQL Server содержатся сведения о нескольких поддерживаемых версиях и разновидностях SQL Server. Возможности могут различаться в зависимости от версии и разновидности SQL Server, поэтому содержимое тоже может различаться. 

Чтобы просматривать только содержимое, относящееся к интересующей вас версии и разновидности SQL Server, можно использовать [фильтр версий](versioning-system-monikers-ui-sql-server.md): 

![Фильтр версий в документации к SQL](media/sql-server-docs-navigation-guide/sql-docs-version-filter.gif)

Если выбрать **All SQL** \> **Hide nothing** (Все по SQL > Ничего не скрывать) будет отображаться все содержимое и ничто не будет скрыто фильтром версий. Если используется параметр **Hide nothing** (Ничего не скрывать), может отображаться содержимое, относящееся к нескольким версиям SQL Server в одной статье, что может привести к противоречию, неоднозначным утверждениям или путанице. Поэтому параметр [**Hide nothing** (Ничего не скрывать) не рекомендуется использовать постоянно](versioning-system-monikers-ui-sql-server.md#anchor-allsql-hidenothing). 

## <a name="breadcrumbs"></a>Строки навигации

Строки навигации находятся под заголовком и над оглавлением. Они указывают место текущей статьи в оглавлении.  Это позволяет определить контекст для текущего содержимого и вернуться на верхние уровни оглавления:

![Строки навигации в документации к SQL](media/sql-server-docs-navigation-guide/sql-docs-bread-crumbs.gif)

## <a name="article-section-navigation"></a>Навигация по разделам статьи

Область навигации справа позволяет быстро переходить к разделам статьи, а также определять, в каком разделе статьи вы сейчас находитесь.  

![Область навигации справа](media/sql-server-docs-navigation-guide/sql-docs-right-hand-navigation.gif)


## <a name="submit-docs-feedback"></a>Отправка отзыва по документации к SQL

Если вы обнаружили ошибку в статье, то можете отправить отзыв в отдел разработки документации по SQL. Для этого прокрутите страницу вниз и выберите пункт **Отзывы о содержимом**.

![отзывы о содержимом в разделе "Проблемы Git"](media/sql-server-get-help/git-issues.png)

Вы также можете отправить общие отзывы и предложения о документации по адресу [https://aka.ms/sqldocsfeedback](https://aka.ms/sqldocsfeedback). 

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

![Правка документации по SQL](media/sql-server-docs-navigation-guide/edit-sql-docs.gif)

## <a name="next-steps"></a>Дальнейшие действия

- Начните работу с [технической документацией по SQL Server](index.yml).
- Дополнительные сведения об отправке отзывов и получении справки по SQL Server см. на странице [получения справки](sql-server-get-help.md). 
- Чтобы быстро получить доступ ко всем кратким руководствам и учебникам, перейдите к статье [Обучающие ресурсы по SQL](../sql-server/educational-sql-resources.yml).
