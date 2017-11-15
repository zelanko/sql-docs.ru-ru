---
title: "Просмотр или изменение расположения по умолчанию для файлов данных и журнала | Документы Майкрософт"
ms.custom: 
ms.date: 06/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: e1afb149a8b3348660e4e21c879598436eaaedfa
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>Просмотр или изменение расположения по умолчанию для файлов данных и журнала
  
 Рекомендуемым способом защиты файлов данных и журналов является защита с помощью списков управления доступом (ACL). Задайте в качестве расположения списков ACL корневой каталог, где создаются файлы.  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>Просмотр или изменение расположений по умолчанию для файлов базы данных  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите **Свойства**.  
  
2.  На странице "Свойства" левой панели откройте вкладку **Параметры базы данных** .  
  
3.  В области **Места хранения, используемые базой данных по умолчанию**можно просмотреть текущие расположения, используемые по умолчанию для новых файлов данных и файлов журнала. Чтобы изменить местоположение по умолчанию, введите новый путь по умолчанию в поле **Данные** или **Журнал** или нажмите кнопку обзора, перейдите к нужному пути и выберите его.  
  
>**ПРИМЕЧАНИЕ.** После смены расположений необходимо остановить и запустить службу SQL Server для завершения изменения.  
  
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Создание базы данных](../../relational-databases/databases/create-a-database.md)  
  
  
