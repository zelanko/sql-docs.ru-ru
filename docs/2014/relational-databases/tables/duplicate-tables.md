---
title: Дублирование таблиц | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- tables [SQL Server], duplicating
- duplicating tables
- table copying [SQL Server]
ms.assetid: c6b07423-d1e5-4e5e-8681-5088921f5df3
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aacd91d44d5d4939ab699b17d4decc124cffcc30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198814"
---
# <a name="duplicate-tables"></a>Дублирование таблиц
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно создать копию существующей таблицы с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] , создав новую таблицу и скопировав в нее сведения о столбцах из существующей таблицы.  
  
> [!IMPORTANT]  
>  Эта операция дублирует только структуру таблицы. При этом не происходит дублирования строк таблицы.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Дублирование таблицы с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение CREATE TABLE в целевой базе данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-duplicate-a-table"></a>Дублирование таблицы  
  
1.  Убедитесь, что есть подключение к базе данных, в которой нужно создать таблицу, и эта база данных выбрана в обозревателе объектов.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши пункт **Таблицы** , а затем выберите **Создать таблицу**.  
  
3.  В обозревателе объектов щелкните правой кнопкой мыши таблицу, которую нужно скопировать, и выберите пункт **Конструктор**.  
  
4.  Выделите столбец из существующей таблицы и в меню **Правка** выберите **Копировать**.  
  
5.  Перейдите в новую таблицу и выберите первую строку.  
  
6.  В меню **Правка** выберите **Вставить**.  
  
7.  В меню **Файл** выберите пункт **Сохранить***имя_таблицы*.  
  
8.  В диалоговом окне **Выбор имени** введите имя новой таблицы и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a>Дублирование таблицы в редакторе запросов  
  
1.  Убедитесь, что есть подключение к базе данных, в которой нужно создать таблицу, и эта база данных выбрана в обозревателе объектов.  
  
2.  Щелкните правой кнопкой таблицу, копию которой необходимо создать, выберите команду **Создать скрипт таблицы как**, укажите **CREATE для**и выберите вариант **Создать окно редактора запросов**.  
  
3.  Измените имя таблицы.  
  
4.  Удалите все столбцы, которые не требуются в новой таблице.  
  
5.  Нажмите кнопку **Выполнить**.  
  
  
