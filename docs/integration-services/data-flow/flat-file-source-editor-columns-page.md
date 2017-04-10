---
title: "Редактор источника &#171;Неструктурированный файл&#187; (страница &#171;Столбцы&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.flatfilesourceadapter.columns.f1"
helpviewer_keywords: 
  - "редактор источника «Неструктурированный файл»"
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Редактор источника &#171;Неструктурированный файл&#187; (страница &#171;Столбцы&#187;)
  С помощью узла **Столбцы** диалогового окна **Редактор источника "Неструктурированный файл"** можно сопоставлять выходной столбец с каждым внешним (исходным) столбцом.  
  
> [!NOTE]  
>  Свойство **FileNameColumnName** источника «Неструктурированный файл» и свойство **FastParse** его выходных столбцов недоступны в **Редакторе источника «Неструктурированный файл»**, однако их можно задать с помощью **Расширенного редактора**. Дополнительные сведения об этих свойствах см. в подразделе «Источник "Неструктурированный файл"» раздела [Flat File Custom Properties](../../integration-services/data-flow/flat-file-custom-properties.md).  
  
 Дополнительные сведения об источнике «Неструктурированный файл» см. в разделе [Flat File Source](../../integration-services/data-flow/flat-file-source.md).  
  
## Параметры  
 **Доступные внешние столбцы**  
 Просмотр списка доступных внешних столбцов источника данных. В этой таблице нельзя добавлять или удалять столбцы.  
  
 **Внешний столбец**  
 Просмотр внешних (исходных) столбцов в том порядке, в котором их будет считывать задача. Этот порядок можно изменить, вначале очистив выделенные столбцы в таблице, а затем выбрав в списке внешние столбцы в другом порядке.  
  
 **Выходной столбец**  
 Введите уникальное имя для каждого выходного столбца. По умолчанию используется имя выбранного внешнего (исходного) столбца, однако можно выбрать любое уникальное описательное имя. Выбранное имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор источника "Неструктурированный файл" (страница "Диспетчер соединений")](../../integration-services/data-flow/flat-file-source-editor-connection-manager-page.md)   
 [Редактор источника "Неструктурированный файл" (страница "Вывод ошибок")](../../integration-services/data-flow/flat-file-source-editor-error-output-page.md)   
 [Диспетчер соединений с неструктурированными файлами](../../integration-services/connection-manager/flat-file-connection-manager.md)  
  
  