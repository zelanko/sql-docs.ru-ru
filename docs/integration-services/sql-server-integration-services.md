---
title: "Службы SQL Server Integration Services | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
keywords: "Службы SSIS"
helpviewer_keywords:
- SSIS
- DTS [Integration Services]
- SQL Server Integration Services
- Integration Services
- DTS [Integration Services], about Integration Services
- data integration [Integration Services]
- Data Transformation Services
ms.assetid: c4398655-5657-4ae4-a690-a380790fe84f
caps.latest.revision: "51"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 2f1580e8d59c391b5721fc89ea2b58712ec34364
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sql-server-integration-services"></a>службы SQL Server Integration Services

 > Содержимое, связанное с предыдущими версиями SQL Server, см. в разделе [Службы SQL Server Integration Services](https://msdn.microsoft.com/library/ms141026(SQL.120).aspx).

[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — это платформа для построения решений по интеграции и преобразованию данных уровня предприятия. Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] используются при решении сложных бизнес-задач путем копирования и загрузки файлов, отправки электронных сообщений в ответ на события, обновления хранилищ данных, очистки и интеллектуального анализа данных, а также управления объектами и данными [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Пакеты могут работать отдельно или совместно с другими пакетами для решения сложных бизнес-задач. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] могут извлекать и преобразовывать данные из ряда таких источников, как файлы XML-данных, неструктурированные файлы и источники реляционных данных, и затем загружать эти данные в один или несколько реляционных объектов.<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] включает широкий набор встроенных задач и преобразований, средства для построения пакетов, а также службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для выполнения пакетов и управления ими. С помощью графических инструменты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] можно создавать готовые решения, не написав ни единой строки кода, либо программировать подробную объектную модель служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для программного создания пакетов и создания в программном коде пользовательских задач и других объектов пакета.

## <a name="try-sql-server-and-sql-server-integration-services"></a>Попробуйте SQL Server и службы SQL Server Integration Services
- [![Скачать из Центра оценки](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=829477) [Скачать SQL Server 2017 или 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server)
- [![Скачать из Evaluation Center](../includes/media/download2.png)](../ssdt/download-sql-server-data-tools-ssdt.md) [Скачать SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- [![Скачать из Evaluation Center](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) [Скачать SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)

##  <a name="infotipsql-servermediainfo-tippng-get-help"></a>![info_tip](../sql-server/media/info-tip.png) получить справку
 
- [Задать вопрос на форуме MSDN, посвященном службам SSIS](https://social.msdn.microsoft.com/Forums/home?forum=sqlintegrationservices)
- [Задать вопрос на форуме MSDN, посвященном SSDT и SSMS](https://social.msdn.microsoft.com/Forums/home?forum=sqltool)
- [Задать вопрос на сайте Stack Overflow (тег *ssis*)](http://stackoverflow.com/questions/tagged/ssis)
- [Microsoft Connect — сообщайте об ошибках и запрашивайте функции](https://connect.microsoft.com/SQLServer/Feedback)
- [Общее обсуждение на сайте Reddit, посвященное службам SSIS](https://www.reddit.com/r/SQLServer/search?q=ssis&restrict_sr=on)
- [Варианты поддержки Майкрософт для бизнес-пользователей](https://support.microsoft.com/gp/support-options-for-business)
- [Варианты обращения в службу поддержки Майкрософт для бизнес-пользователей](https://support.microsoft.com/gp/contactus81?Audience=Commercial)
