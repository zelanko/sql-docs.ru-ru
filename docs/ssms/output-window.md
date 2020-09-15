---
description: Окно вывода в SQL Server Management Studio
title: Окно вывода в SSMS
ms.custom: seo-lt-2019
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Output Window [SQL Server Management Studio]
- Activity Monitor [SQL Server Management Studio]
- Object Explorer [SQL Server Management Studio]
ms.assetid: a2ce1a07-b4e2-471c-87d2-b8de5e6c6864
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 98a7e2695c2327e26043ef9bf3e4f1578e7abfe6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88316970"
---
# <a name="output-window-in-sql-server-management-studio"></a>Окно вывода в SQL Server Management Studio
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Окно вывода можно открыть из меню "Вид" или с помощью сочетания клавиш CTRL+ALT+O. Существует несколько каналов выходных данных.

В следующей таблице представлен обзор типов сообщений, связанных с каждым каналом выходных данных.

|Канал|Описание|
|-----------|---------------|  
|**Телеметрия**|Телеметрия — это поток [анонимных данных об использовании функций](sql-server-management-studio-ssms.md), собираемых корпорацией Майкрософт. Вы можете использовать эти события для сохранения собственных данных об использовании SSMS. Они помогают определить, какие узлы обозревателя объектов были развернуты и какие команды запускались в сеансе SSMS, пока было открыто окно вывода.|
|**Обозреватель объектов**|В этом канале выводится текст и затраченное время запросов SQL, необходимых для разворачивания узлов в обозревателе объектов. Каждый запрос записывает в журнал события начала и окончания запроса. У каждого события есть метка времени и универсальное имя ресурса, связанное с запрашиваемой сущностью. [Универсальное имя ресурса (URN)](https://technet.microsoft.com/library/microsoft.sqlserver.management.smo.urn(v=sql.90).aspx) ссылается на управляющий объект SQL Server и включает иерархию типа XPath. Например, URN для таблицы с именем "Table1" в базе данных "Db" на сервере "MyServer" будет иметь вид "Server[@Name='MyServer']/Database[@Name='Db']/Table[/@Name='Table1']". При разворачивании одного узла в обозревателе объектов возможно выполнение множества таких запросов с разными параметрами. Событие окончания запроса будет содержать затраченное время и текст TSQL. Эти данные могут быть полезны для анализа производительности сервера в тех случаях, когда какой-то узел в обозревателе объектов разворачивается слишком медленно. **Примечание**. Такие подробные сведения о запросах предоставляются не для всех узлов в обозревателе объектов.|
|**Монитор активности**|Этот канал запускается при [открытии Монитора активности](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor) для сервера. Этот поток содержит события, включающие часть текста запроса и временную отметку для каждого запроса, сообщения об ошибках и уведомления о приостановке монитора из-за проблем с подключением. Если монитор активности не отвечает или не обновляется, проверьте этот выходной канал для получения дополнительных сведений.|





