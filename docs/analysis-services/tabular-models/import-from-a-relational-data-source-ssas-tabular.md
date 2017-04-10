---
title: "Импорт из реляционного источника данных (табличные службы SSAS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Импорт из реляционного источника данных (табличные службы SSAS)
  С помощью мастера импорта таблиц можно импортировать данные из разных реляционных баз данных: Этот мастер доступен в меню [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Модель ** ** . Для соединения с источником данных на компьютере должен быть установлен соответствующий поставщик. Дополнительные сведения о поддерживаемых источниках данных и поставщиках см. в разделе [Поддерживаемые источники данных (табличные службы SSAS)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md).  
  
 Мастер импорта таблиц поддерживает импорт данных из следующих источников данных:  
  
 **Реляционные базы данных**  
  
-   База данных Microsoft SQL Server  
  
-   Microsoft SQL Azure  
  
-   База данных Microsoft Access  
  
-   Параллельные хранилища данных Microsoft SQL Server  
  
-   Oracle;  
  
-   Teradata  
  
-   Sybase  
  
-   Informix  
  
-   IBM DB2  
  
-   OLE DB/ODBC  
  
 **Многомерные источники**  
  
-   Куб служб Microsoft SQL Server Analysis Services  
  
 Мастер импорта таблиц не поддерживает импорт данных из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в качестве источника данных.  
  
### Импорт данных из базы данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.  
  
2.  На странице **Подключение к источнику данных** выберите тип базы данных для подключения и нажмите кнопку **Далее**.  
  
3.  Выполните шаги мастера импорта таблиц. На последующих страницах можно будет выбрать отдельные таблицы и представления или применить фильтры на странице **Выбор таблиц и представлений** или с помощью создания SQL-запроса на странице **Указание SQL-запроса** .  
  
## См. также  
 [Импорт данных (табличные службы SSAS)](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)   
 [Поддерживаемые источники данных (табличные службы SSAS)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  