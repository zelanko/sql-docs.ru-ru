---
title: Окно вывода SSMS | Microsoft Docs
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: a070121a50f056ad293bc4aec6af305587a9b6c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65095670"
---
# <a name="output-window-in-sql-server-management-studio"></a>Окно вывода в SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Окно вывода можно открыть из меню "Вид" или с помощью сочетания клавиш CTRL+ALT+O. Существует несколько каналов выходных данных.

В следующей таблице представлен обзор типов сообщений, связанных с каждым каналом выходных данных.

|Channel|Описание|
|-----------|---------------|  
|**Телеметрия**|Телеметрия — это поток [анонимных данных об использовании функций](sql-server-management-studio-ssms.md), собираемых корпорацией Майкрософт. Вы можете использовать эти события для сохранения собственных данных об использовании SSMS. Они помогают определить, какие узлы обозревателя объектов были развернуты и какие команды запускались в сеансе SSMS, пока было открыто окно вывода.|
|**Обозреватель объектов**|В этом канале выводится текст и затраченное время запросов SQL, необходимых для разворачивания узлов в обозревателе объектов. Каждый запрос записывает в журнал события начала и окончания запроса. У каждого события есть метка времени и универсальное имя ресурса, связанное с запрашиваемой сущностью. [Универсальное имя ресурса (URN)](https://technet.microsoft.com/library/microsoft.sqlserver.management.smo.urn(v=sql.90).aspx) ссылается на управляющий объект SQL Server и включает иерархию типа XPath. Например, URN для таблицы с именем "Table1" в базе данных "Db" на сервере "MyServer" будет иметь вид "Server[@Name='MyServer']/Database[@Name='Db']/Table[/@Name='Table1']". При разворачивании одного узла в обозревателе объектов возможно выполнение множества таких запросов с разными параметрами. Событие окончания запроса будет содержать затраченное время и текст TSQL. Эти данные могут быть полезны для анализа производительности сервера в тех случаях, когда какой-то узел в обозревателе объектов разворачивается слишком медленно. **Примечание**. Такие подробные сведения о запросах предоставляются не для всех узлов в обозревателе объектов.|
|**Монитор активности**|Этот канал запускается при [открытии Монитора активности](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor) для сервера. Этот поток содержит события, включающие часть текста запроса и временную отметку для каждого запроса, сообщения об ошибках и уведомления о приостановке монитора из-за проблем с подключением. Если монитор активности не отвечает или не обновляется, проверьте этот выходной канал для получения дополнительных сведений.|





