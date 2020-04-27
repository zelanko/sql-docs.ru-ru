---
title: Импорт из реляционного источника данных (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 61fb30ea21ea810eab8d30a3a040fac4a1bd2128
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66080525"
---
# <a name="import-from-a-relational-data-source-ssas-tabular"></a>Импорт из реляционного источника данных (табличные службы SSAS)
  С помощью мастера импорта таблиц можно импортировать данные из разных реляционных баз данных: Этот мастер доступен в меню [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Модель **** . Для соединения с источником данных на компьютере должен быть установлен соответствующий поставщик. Дополнительные сведения о поддерживаемых источниках данных и поставщиках см. в разделе [Поддерживаемые источники данных (табличные службы SSAS)](tabular-models/data-sources-supported-ssas-tabular.md).  
  
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
  
 Мастер импорта таблиц не поддерживает импорт данных из книги [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] в качестве источника данных.  
  
### <a name="to-import-data-from-a-database"></a>Импорт данных из базы данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.  
  
2.  На странице **Подключение к источнику данных** выберите тип базы данных для подключения и нажмите кнопку **Далее**.  
  
3.  Выполните шаги мастера импорта таблиц. На последующих страницах можно будет выбрать отдельные таблицы и представления или применить фильтры на странице **Выбор таблиц и представлений** или с помощью создания SQL-запроса на странице **Указание SQL-запроса** .  
  
## <a name="see-also"></a>См. также  
 [Импорт данных &#40;табличные&#41;SSAS](import-data-ssas-tabular.md)   
 [Поддерживаемые источники данных (табличные службы SSAS)](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
