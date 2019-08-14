---
title: Руководство по навигации в документации по SQL Server
description: В руководстве по навигации в технической документации по SQL Server рассматриваются такие элементы, как главная страница, оглавление, заголовок, а также использование адресной строки и фильтра версий.
ms.date: 07/11/2019
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || >= sql-server-linux-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: e5a3e33d48b70146b439790e6439ef4f9cac08b5
ms.sourcegitcommit: c2052b2bf7261b3294a3a40e8fed8b9e9c588c37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/10/2019
ms.locfileid: "68941163"
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

## <a name="toc-navigation-hints"></a>Указания по навигации в оглавлении

Если в конце пункта оглавления есть значок `>`, это означает, что при переходе вы покинете сайт docs.microsoft.com. 

![Одинарный значок в оглавлении](media/sql-server-docs-navigation-guide/single-carrots-in-sql-docs-toc.png)


Если в конце пункта оглавления есть значок `>>`, это означает, что вы перейдете к технической документации с другим оглавлением. 

![Маркеры навигации по оглавлению](media/sql-server-docs-navigation-guide/double-carrots-in-sql-docs-toc.png)

Если вы перейдете на одну из этих страниц, то можете вернуться на главную страницу и в оглавление технической документации по SQL Server, выбрав пункт "Добро пожаловать в SQL Server >>", который находится вверху каждого оглавления. 

![Возвращение в оглавление документации по SQL](media/sql-server-docs-navigation-guide/navigate-back-to-sql-toc.png)

## <a name="toc-search-tip"></a>Советы по поиску в оглавлении
На сайте docs.microsoft.com можно вести поиск по оглавлению с помощью поля фильтра поиска в верхней части страницы: 

![Использование поля фильтра](media/sql-server-docs-navigation-guide/sql-docs-toc-filter.gif)

## <a name="version-filter"></a>Фильтр версий
В технической документации по SQL Server содержатся сведения о нескольких поддерживаемых версиях и разновидностях SQL Server. Возможности могут различаться в зависимости от версии и разновидности SQL Server, поэтому содержимое тоже может различаться. 

Чтобы просматривать только содержимое, относящееся к интересующей вас версии и разновидности SQL Server, можно использовать фильтр версий: 

![Фильтр версий в документации к SQL](media/sql-server-docs-navigation-guide/sql-docs-version-filter.gif)

При выборе **Весь SQL** > **Ничего не скрывать** будет отображаться все содержимое и ничто не будет скрыто фильтром версий. 

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

## <a name="next-steps"></a>Следующие шаги

- Начните работу с [технической документацией по SQL Server](sql-server-technical-documentation.md). 
- Дополнительные сведения об отправке отзывов и получении справки по SQL Server см. на странице [получения справки](sql-server-get-help.md). 
- Чтобы быстро получить доступ ко всем кратким руководствам и учебникам, перейдите в [центр обучения SQL Server](../lp/sql-server/sql-education-center.md).
