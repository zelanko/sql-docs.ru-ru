---
title: "Редактор источника &#171;ADO.NET&#187; (страница &#171;Столбцы&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.adonetsource.columns.f1"
ms.assetid: fbc205b9-2001-4737-a76b-1ba777344bd9
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Редактор источника &#171;ADO.NET&#187; (страница &#171;Столбцы&#187;)
  Страница **Столбцы** диалогового окна **Редактор источника "ADO.NET"** используется для сопоставления выходного столбца с каждым внешним (исходным) столбцом.  
  
 Дополнительные сведения об источниках данных «ADO.NET» см. в разделе [ADO NET Source](../../integration-services/data-flow/ado-net-source.md).  
  
 **Открытие страницы «Столбцы»**  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий источник данных «ADO.NET».  
  
2.  На вкладке **Поток данных** дважды щелкните источник данных "ADO.NET".  
  
3.  В окне **Редактор источника «ADO.NET»**нажмите кнопку **Столбцы**.  
  
## Параметры  
 **Доступные внешние столбцы**  
 Просмотр списка доступных внешних столбцов источника данных. В этой таблице нельзя добавлять или удалять столбцы.  
  
 **Внешний столбец**  
 Просмотрите внешние столбцы (столбцы в источнике) в том порядке, в котором они отображаются при настройке компонентов, получающих данные из этого источника.  
  
 **Выходной столбец**  
 Введите уникальное имя для каждого выходного столбца. По умолчанию используется имя выбранного внешнего (исходного) столбца, однако можно выбрать любое уникальное описательное имя. Это имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
## См. также  
 [Редактор источника "ADO.NET" (страница "Диспетчер подключений")](../../integration-services/data-flow/ado-net-source-editor-connection-manager-page.md)   
 [Редактор источника данных "ADO.NET" (страница "Вывод ошибок")](../../integration-services/data-flow/ado-net-source-editor-error-output-page.md)   
 [Диспетчер соединений ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)  
  
  