---
title: Импорт из реляционного источника данных (табличные службы SSAS) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6dfbcd0b047e45bf94eab9a9916fc47d60a688e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101420"
---
# <a name="import-from-a-relational-data-source-ssas-tabular"></a>Импорт из реляционного источника данных (табличные службы SSAS)
  С помощью мастера импорта таблиц можно импортировать данные из разных реляционных баз данных: Этот мастер доступен в меню **Модель** [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Для соединения с источником данных на компьютере должен быть установлен соответствующий поставщик. Дополнительные сведения о поддерживаемых источниках данных и поставщиках см. в разделе [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
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
 [Импорт данных &#40;табличные службы SSAS&#41;](import-data-ssas-tabular.md)   
 [Поддерживаемые источники данных &#40;табличные службы SSAS&#41;](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  