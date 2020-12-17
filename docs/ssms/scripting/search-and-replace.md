---
title: Поиск и замена
description: Узнайте о четырех различных способах поиска и замены текста, каждый из которых использует собственную версию диалогового окна "Найти и заменить". Параметры поиска и замены влияют на все эти способы поиска.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: ssms
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- match case [SQL Server]
- undo operations
- searches [SQL Server Management Studio]
- replacing text
- quick search and replaces [SQL Server Management Studio]
- Query Editor [SQL Server Management Studio], undo
- Query Editor [SQL Server Management Studio], searching
- regular expressions [SQL Server Management Studio]
- finding text [SQL Server Management Studio]
- text [SQL Server], search and replace operations
- finding [SQL Server Management Studio]
- locating text
- Query Editor [SQL Server Management Studio], replacing text
- Find and Replace dialog box
- wildcard options [SQL Server Management Studio]
- match whole word [SQL Server]
- searches [SQL Server Management Studio], replacing
ms.assetid: 3641c7b3-3e3e-4ddd-af82-c15b50004f94
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 57c1046904904ecdad16de1ea9f3c08ea46d8dcb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97466295"
---
# <a name="search-and-replace"></a>Поиск и замена
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  Существует несколько способов поиска и замены текста. Пункт **Найти и заменить** из меню **Правка** содержит четыре команды: **Быстрый поиск**, **Быстрая замена**, **Найти в файлах** и **Заменить в файлах**. Каждая из этих команд открывает диалоговое окно **Найти и заменить** . Можно выполнить поиск и без диалогового окна с помощью сочетаний клавиш добавочного поиска. Эти методы позволяют управлять областью поиска и замены, а также выбирать способ просмотра совпадений при поиске и замене.  
  
 Выполняя поиск и замену текста, необходимо учитывать следующее.  
  
-   Параметры, установленные в диалоговом окне **Найти и заменить** , влияют на все поиски. В числе этих параметров такие, как **Учитывать регистр**, **Слово целиком**, **Искать вверх**, **Искать скрытый текст**, **Подстановочные знаки**, **Регулярные выражения**, **Искать во всех открытых документах** и **Искать в текущем проекте**. Не все эти параметры доступны во всех версиях диалогового окна **Найти и заменить** ;  
  
-   Кнопка **Отмена** доступна только для документов, оставшихся открытыми после операции замены.  
  
-   Команда **Отменить** для операции **Заменить все** , выполняемой над несколькими файлами, рассматривается как единичное массовое действие над всеми затронутыми файлами. При этом нельзя отменить изменения в одних файлах, сохранив их в других.  
  
 Обычно нельзя выполнять поиск в элементах с графическим отображением.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение добавочного поиска в активном документе](./search-an-active-document-incrementally.md)   
 [осуществлять поиск в документах в интерактивном режиме](./search-documents-interactively.md)   
 [Поиск документов с помощью списков результатов](./search-documents-using-results-lists.md)   
 [Поиск текста с символами-шаблонами](./search-text-with-wildcards.md)   
 [Поиск текста с помощью регулярных выражений](./search-text-with-regular-expressions.md)  
  
