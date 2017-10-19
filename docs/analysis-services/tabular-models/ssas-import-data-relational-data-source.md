---
title: "Импорт из реляционного источника данных (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 10/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: d45d72ca09a8abce6d29f018fcbaa8f54415a637
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="import-data---relational-data-source"></a>Импорт данных - источник реляционных данных
  Для табличных моделей на 1200 и более низких уровнях совместимости можно импортировать данные из разнообразных реляционных баз данных с помощью мастера импорта таблиц. Этот мастер доступен в меню [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Модель ****  . Для соединения с источником данных на компьютере должен быть установлен соответствующий поставщик. Дополнительные сведения о поддерживаемых источниках данных и поставщиках см. в разделе [Поддерживаемые источники данных (табличные службы SSAS)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md). 
 
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
  
### <a name="to-import-data-from-a-database"></a>Импорт данных из базы данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.  
  
2.  На странице **Подключение к источнику данных** выберите тип базы данных для подключения и нажмите кнопку **Далее**.  
  
3.  Выполните шаги мастера импорта таблиц. На последующих страницах можно будет выбрать отдельные таблицы и представления или применить фильтры на странице **Выбор таблиц и представлений** или с помощью создания SQL-запроса на странице **Указание SQL-запроса** .  
  
## <a name="see-also"></a>См. также  
 [Импорт данных (табличные службы SSAS)](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [Поддерживаемые источники данных (табличные службы SSAS)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  

