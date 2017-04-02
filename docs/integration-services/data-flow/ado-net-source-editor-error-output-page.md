---
title: "Редактор источника данных &#171;ADO.NET&#187; (страница &#171;Вывод ошибок&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.adonetsource.erroroutput.f1"
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Редактор источника данных &#171;ADO.NET&#187; (страница &#171;Вывод ошибок&#187;)
  Страница **Вывод ошибок** диалогового окна **Редактор источника «ADO.NET»** используется для выбора параметров обработки ошибок, а также для установки свойств выходных столбцов ошибок.  
  
 Дополнительные сведения об источниках данных «ADO.NET» см. в разделе [ADO NET Source](../../integration-services/data-flow/ado-net-source.md).  
  
 **Открытие страницы «Вывод ошибок»**  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий источник данных «ADO.NET».  
  
2.  На вкладке **Поток данных** дважды щелкните источник данных "ADO.NET".  
  
3.  В окне **Редактор источника «ADO.NET»**нажмите кнопку **Вывод ошибок**.  
  
## Параметры  
 **Ввод-вывод**  
 Просмотр имени источника данных.  
  
 **Столбец**  
 Просмотрите внешние (исходные) столбцы, выбранные на странице **Диспетчер подключений** диалогового окна **Редактор источника "ADO.NET"**.  
  
 **Ошибка**  
 Задайте действие, которое необходимо выполнить при возникновении ошибки: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **См. также:** [Обработка ошибок в данных](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **Усечение**  
 Укажите, что нужно сделать при усечении: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Description**  
 Просмотреть описание ошибки.  
  
 **Присвоить указанное значение выбранным ячейкам**  
 Укажите действие, которое необходимо применить ко всем выбранным ячейкам при возникновении ошибки или усечения: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Применить**  
 Применить параметр обработки ошибок к выбранным ячейкам.  
  
## См. также  
 [Редактор источника "ADO.NET" (страница "Диспетчер подключений")](../../integration-services/data-flow/ado-net-source-editor-connection-manager-page.md)   
 [Редактор источника "ADO.NET" (страница "Столбцы")](../../integration-services/data-flow/ado-net-source-editor-columns-page.md)   
 [Диспетчер соединений ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)  
  
  