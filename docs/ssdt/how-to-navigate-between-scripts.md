---
title: переходить между скриптами
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.editor.howto.navigate
ms.assetid: 8664bde5-86ff-4e8b-b5a6-af003316f6ad
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 910011609e928efe9180a3aa4f041aa063adbab4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75241382"
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
  
