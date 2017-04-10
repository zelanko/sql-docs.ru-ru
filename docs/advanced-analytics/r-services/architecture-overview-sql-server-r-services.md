---
title: "Обзор архитектуры (службы SQL Server R) | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c4a4f66-ea3e-4a73-acf2-6c8aeafc94b0
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 9
---
# Обзор архитектуры (службы SQL Server R)
В этом разделе содержится обзор архитектуры [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], включая безопасность, новые компоненты, добавляемые в компоненте SQL Server database engine компонентов для поддержки R и взаимодействие скриптов R с открытым исходным, работающей на SQL Server.


## Цели


Архитектура [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] поддерживает язык R с открытым кодом. Текущие пользователи R сможете перенести свой код R и его выполнение с относительно небольшими изменениями в T-SQL.

Тем не менее R служб SQL Server также предоставляет инновации, которые дают повышения производительности и более тесную интеграцию базы данных для языка R, чтобы быстрее пропускная способность и обработки, а также снижения барьеры для разработки корпоративных решений R. Эти нововведения включают открытым исходным кодом и собственных компонентов, разработанных корпорацией Майкрософт.


Основной целью интеграции с сервером SQL Server, для обеспечения повышения производительности и масштабируемости для R, но безопасного управления данными. К этой цели R служб SQL Server предоставляет инфраструктуру несколькими процессами, поддерживающий встроенную проверку подлинности Windows и на основе паролей имен входа SQL Server. 

+ [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] Предоставляет базовый распределение R, вместе с пакетами проекционная и возможность параллельного выполнения задач R.
+ Новые компоненты SQL Server предоставляют платформу, безопасный, высокопроизводительный внешних сценариев.
+ R задачи выполняются вне процесса SQL Server, чтобы обеспечить безопасность и Повышенная управляемость.
+ [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Управляет безопасности все процессы R. 

Чтобы помочь вам оптимизировать существующий код на R и использовать преимущества этих улучшений, в этом разделе описываются подробно новой архитектуры. Как обработка и анализ данных обрабатывается понимание [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], вы можете выбрать соответствующую о приема данных, наиболее эффективно выполнить реконструирование признаков и использовать результаты.
 

## В этом разделе
+ [Взаимодействие R](../../advanced-analytics/r-services/r-interoperability-in-sql-server-r-services.md)
+ [Новые компоненты SQL Server для служб R](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)
+ [Общие сведения о безопасности](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md)

## См. также:
[Учебники по службам Services R](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)
