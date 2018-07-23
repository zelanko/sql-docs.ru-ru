---
title: Практическое руководство. Навигация между скриптами | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.editor.howto.navigate
ms.assetid: 8664bde5-86ff-4e8b-b5a6-af003316f6ad
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b06fbf69aa5a9d1c9354907f953d0fa98e8f9d40
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085676"
---
# <a name="how-to-navigate-between-scripts"></a>Навигация между скриптами
В редакторе Transact\-SQL для автономной разработки есть два полезных навигационных средства, с которыми знакомы пользователи Visual Studio: "Перейти к определению" и "Найти все ссылки". Например, можно щелкнуть правой кнопкой мыши имя таблицы и выбрать «Найти все ссылки», чтобы вывести список всех ссылок на таблицу в проекте. Можно дважды щелкнуть результат поиска для перехода к конкретному файлу кода. В этом файле можно еще раз щелкнуть имя таблицы правой кнопкой мыши, выбрать «Перейти к определению» и вернуться обратно к определению таблицы.  
  
> [!WARNING]  
> В следующих процедурах используются сущности, которые созданы в рамках процедур, описанных в руководствах по [разработке подключенной базы данных](../ssdt/connected-database-development.md) и [автономной разработке базы данных с учетом проекта](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-navigate-between-scripts"></a>Навигация между скриптами  
  
1.  Разверните папку **Функции** в **обозревателе решений** и дважды щелкните **GetProductsBySupplier.sql**.  
  
2.  Щелкните правой кнопкой мыши `Products` в этой строке кода и выберите **Перейти к определению**.  
  
    ```  
    SELECT * from Products p  
    ```  
  
3.  Products.SQL будет автоматически открыт с указанием места, где определен тип `Products`.  
  
4.  Вернитесь к GetProductsBySupplier.sql. Выберите **Найти все ссылки** в контекстном меню для `Products`. В области **Результаты поиска символа** панели отобразится список мест, содержащих ссылки на таблицу `Products`. Дважды щелкните любой из результатов поиска, чтобы перейти к расположению соответствующей ссылки.  
  
