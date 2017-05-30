---
title: "Базы данных и таблицы Stretch — помощник базы данных Stretch | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/14/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, identifying databases
- Stretch Database, identifying tables
- identifying databases for Stretch Database
- identifying tables for Stretch Database
ms.assetid: 81bd93d8-eef8-4572-88d7-5c37ab5ac2bf
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 603226ee369f6e557bae19e80211677f92fe7cd7
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="stretch-database-databases-and-tables---stretch-database-advisor"></a>Базы данных и таблицы Stretch — помощник базы данных Stretch
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Чтобы указать базы данных и таблицы, подходящие для базы данных Stretch, скачайте помощник по обновлению SQL Server 2016 и запустите помощник базы данных Stretch. Кроме того, помощник базы данных Stretch обнаруживает критические препятствия.  
  
## <a name="download-and-install-upgrade-advisor"></a>Скачивание и установка помощника по обновлению  
 Скачайте и установите помощник по обновлению, перейдя по [ссылке](https://www.microsoft.com/en-us/download/details.aspx?id=53595). Этот инструмент не входит в комплект на установочном носителе [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] .  
  
## <a name="run-the-stretch-database-advisor"></a>Запуск помощника базы данных Stretch  
  
1.  Запустите помощник по обновлению.  
  
2.  Выберите **Сценарии**и щелкните **RUN STRETCH DATABASE ADVISOR**(ЗАПУСТИТЬ ПОМОЩНИК БАЗЫ ДАННЫХ STRETCH).  
  
3.  В колонке **Run Stretch Database Advisor** (Запустить помощник базы данных Stretch) щелкните **SELECT DATABASES TO ANALYZE**(ВЫБРАТЬ БАЗЫ ДАННЫХ ДЛЯ АНАЛИЗА).  
  
4.  В колонке **Выбор базы данных** введите или выберите имя сервера и данные для проверки подлинности. Нажмите кнопку **Соединить**.

5.  Откроется список баз данных на выбранном сервере. Выберите базу данных для анализа. Нажмите кнопку **Выбрать**.  
  
6.  В колонке **Run Stretch Database Advisor** (Запустить помощник базы данных Stretch) щелкните **Запустить**,  чтобы начать анализ.  
  
## <a name="review-the-results"></a>Просмотр результатов  
  
1.  По завершении анализа выберите в колонке **Помощник базы данных Stretch** одну из баз данных, чтобы отобразить колонку **Результаты анализа** .  
  
     В колонке **Результаты анализа** перечислены рекомендуемые таблицы в выбранной базе данных, соответствующие критериям рекомендаций по умолчанию. 
  
2.  В списке таблиц колонки **Результаты анализа** выберите одну из рекомендуемых таблиц, чтобы отобразить колонку **Результаты для таблицы** .  
  
     Если есть проблемы блокировки, в колонке **Результаты для таблицы** перечислены критические препятствия для выбранной таблицы. Сведения о критических препятствиях, обнаруженных помощником базы данных Stretch, см. в статье [Ограничения для базы данных Stretch](../../sql-server/stretch-database/limitations-for-stretch-database.md).  
  
3.  В списке проблем блокировки в колонке **Результаты для таблицы** выберите одну из проблем, чтобы отобразить дополнительные сведения о проблеме и предлагаемые шаги по ее устранению. Выполните предложенные шаги по устранению, если вы хотите настроить выбранную таблицу для базы данных Stretch.  
  
## <a name="next-step"></a>Следующий шаг  
 Включите базу данных Stretch.  
  
-   Сведения о включении базы данных Stretch для **базы данных**см. в разделе [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
-   Сведения о включении базы данных Stretch для другой **таблицы**см. в разделе [Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md). 
  
## <a name="see-also"></a>См. также:  
 [Ограничения для базы данных Stretch](../../sql-server/stretch-database/limitations-for-stretch-database.md)   
 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Настройка базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)  
  
  

