---
title: "Шаг 9. Проверка учебного пакета, созданного на занятии 1 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Шаг 9. Проверка учебного пакета, созданного на занятии 1
На этом занятии были выполнены представленные ниже задачи.  
  
-   Был создан проект служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
-   Была выполнена настройка диспетчеров соединений, используемых пакетом для подключения к исходным и целевым данным.  
  
-   Был добавлен поток данных, который получает данные от источника «неструктурированный файл», производит необходимые преобразования «Уточняющий запрос» и настраивает данные для назначения.  
  
Создание пакета завершено. Теперь необходимо проверить пакет.  
  
## Проверка макета пакета  
Прежде чем проверить пакет, нужно убедиться в том, что потоки данных и управления в пакете занятия 1 содержат объекты, показанные на следующих диаграммах.  
  
**Поток управления**  
  
![Control flow in package](../integration-services/media/task9lesson1control.gif "Control flow in package")  
  
**Поток данных**  
  
![Data flow in package](../integration-services/media/task9lesson1data.gif "Data flow in package")  
  
### Выполнение учебного пакета занятия 1  
  
1.  В меню **Отладка** выберите команду **Начать отладку**.  
  
    В результате запуска пакета к таблице фактов **FactCurrency** в базе данных **AdventureWorksDW2012**будет добавлено 1097 строк.  
  
2.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
## Следующее занятие  
[Занятие 2. Добавление циклов с помощью служб SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## См. также:  
[Запуск проектов и пакетов](../Topic/Execution%20of%20Projects%20and%20Packages.md)  
  
  
  
