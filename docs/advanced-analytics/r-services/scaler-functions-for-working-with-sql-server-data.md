---
title: "Проекционная функции для работы с базами данных SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 5f3c9864-9c75-4688-947d-0940045b2671
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# Проекционная функции для работы с базами данных SQL Server
Здесь представлен обзор основных функций проекционная для использования с SQL Server вместе с комментарии в синтаксисе.

Полный список функций проекционная и способы их использования см. в разделе [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/index#) ссылку в библиотеке MSDN. 

## Функции для работы с источниками данных SQL Server
Следующие функции позволяют определить [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] источника данных. Объект источника данных — это контейнер, который указывает строку подключения вместе с набором данных, который будет определен как таблица, представление или запрос. Вызовы хранимых процедур не поддерживаются.  

Кроме определения источника данных, можно выполнять инструкции DDL с R, при наличии необходимых разрешений на экземпляр и базы данных. 
+ [RxSqlServerData](https://msdn.microsoft.com/microsoft-r/scaler/RxSqlServerData) -Определение [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] объекта источника данных
+ [rxSqlServerDropTable](https://msdn.microsoft.com/microsoft-r/scaler/rxSqlServerDropTable) -Удалить [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] таблицу
+ [rxSqlServerTableExists](https://msdn.microsoft.com/microsoft-r/scaler/rxSqlServerTableExists) -Проверить наличие таблицы базы данных или объекта
+ [rxExecuteSQLDDL](https://msdn.microsoft.com/microsoft-r/scaler/rxExecuteSQLDDL) — выполните команду, чтобы определить, управления и контроля данных SQL, но не возвращают данные  

## Функции для определения или управление контекстом вычислений
Следующие функции используются для определения нового контекста вычисления, переключения контекстов вычислений или определить текущий контекст вычисления.
+ [RxComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/RxComputeContext) -создать контекст вычисления. 
+ [rxInSqlServer](https://msdn.microsoft.com/microsoft-r/scaler/rxInSqlServer) -контекст вычисления SQL Server, который позволяет создавать **проекционная** запуска функции R служб SQL Server.
+ [rxGetComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/rxGetComputeContext) -Получение текущего контекста вычисления. 
+ [rxSetComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/rxSetComputeContext) -указать, какие вычислительные контекст для использования. 

## Функции для использования источника данных
После создания объекта источника данных, можно открыть его для получения данных или записать на него новые данные. В зависимости от размера данных в источнике можно также определить размер пакета как часть источника данных и перемещения данных в виде фрагментов. 
+ [rxIsOpen](https://msdn.microsoft.com/microsoft-r/scaler/rxIsOpen) -Проверьте, доступен ли источник данных
+ [rxOpen](https://msdn.microsoft.com/microsoft-r/scaler/rxOpen) -Открыть источник данных для чтения
+ [rxReadNext](https://msdn.microsoft.com/microsoft-r/scaler/rxReadNext) -считывать данные из источника
+ [rxWriteNext](https://msdn.microsoft.com/microsoft-r/scaler/rxWriteNext) -записывать данные в целевой объект
+ [rxClose](https://msdn.microsoft.com/microsoft-r/scaler/rxclose) -Закрыть источника данных

Дополнительные сведения о работе с этими функциями проекционная может работать с источниками данных, отличного от [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], в разделе [ R Microsoft Server - Приступая к работе](http://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started).

## Функции, которые работают с файлами XDF
Следующие функции можно использовать для создания локального кэша данных в формате XDF. Этот файл может быть полезно при работе с больше данных, чем может быть перемещена из базы данных в один пакет или больше данных, чем может поместиться в памяти.

Если вы регулярно перемещения больших объемов данных из базы данных на локальной рабочей станции, вместо запроса базы данных несколько раз для каждой операции R можно использовать файл XDF для сохранения данных локально и затем работать с ними в рабочей области R, используя файл XDF в качестве кэша.

+ `rxImport` -Перемещение данных из источника ODBC в файл XDF
+ `RxXdfData` -Создание объекта данных XDF
+ `RxDataStep` -Чтение данных из XDF int блок данных
+ `rxXdfToDataFrame` -Чтение данных из XDF в блок данных
+ `rxReadXdf` — Считывает данные из XDF в блок данных

Пример использования файлов XDF, см. в этом учебнике:  [данных наук глубокое погружение - с помощью функции проекционная](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)

Дополнительные сведения об этих функциях проекционная, которые можно использовать для передачи данных из различных источников, в разделе[ R Microsoft Server - Приступая к работе](http://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started).

## См. также:
[Сравнение базы R и функции проекционная](https://msdn.microsoft.com/microsoft-r/scaler/compare-base-r-scaler-functions)
