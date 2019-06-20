---
title: Копирование удаленных таблиц - Parallel Data Warehouse | Документация Майкрософт
description: С помощью копирования удаленной таблицы в Analytics платформы системы Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5ed517a471368e4192ad7393a92274424d37f975
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62678564"
---
# <a name="remote-table-copy"></a>Копирование удаленных таблиц
Описывает способы использования функцией копирования удаленной таблицы для копирование таблиц из базы данных SQL Server PDW в удаленных базах данных SMP SQL Server (не являющийся устройством). Копирование удаленных таблиц к сценариям звездообразной позволяет используйте для SQL Server PDW.  
  
## <a name="BasicsPDE"></a>Общие сведения о копирования удаленной таблицы для SQL Server PDW  
Копирование удаленных таблиц — это функция SQL Server PDW, позволяет реализовать сценарии звездообразной копируя результаты SQL-инструкцию SELECT на таблицу в базе данных SMP. Копирование удаленных таблиц инициируется с [создать REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) инструкции.  
  
## <a name="BasicsPrerequisites"></a>Требования к использованию копирование удаленных таблиц  
Таблицы копирования для копирования удаленной таблицы из SQL Server PDW в базе данных SQL Server можно использовать при выполнении этих условий:  
  
-   Целевой базы данных должен представлять собой экземпляр Microsoft® SQL Server®, на котором выполняется в системе Microsoft Windows®, которая может подключаться к SQL Server PDW appliance, но не находится на сервере в пределах устройства. Удаленный экземпляр SQL Server может подключаться к сети InfiniBand SQL Server PDW или через сеть Ethernet.  
  
-   Данные для копирования должен быть один допустимый SQL Server PDW с помощью [ВЫБЕРИТЕ](../t-sql/queries/select-transact-sql.md) инструкции.  
  
-   Целевой сервер не должен быть устройством. Не удается скопировать данные непосредственно с одного устройства на другой с помощью инструкций в этом разделе.  
  
-   Конечный сервер должны быть доступны всем узлам в сети Infiniband устройства.  
  
## <a name="ConfigureRemote"></a>Настройка копирования удаленной таблицы  
Чтобы использовать копирование удаленных таблиц, вы должны приобрести и настроить сервер Windows, настройки SQL Server на сервере Windows и настроить SQL Server PDW. Используйте следующие ссылки для выполнения этих трех этапов настройки.  
  
1.  [Настройки Windows внешние системы для получения копий удаленных таблиц с помощью InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [Настройка внешнего SMP SQL Server для получения копий удаленных таблиц](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [Настройка SQL Server PDW для копий удаленных таблиц](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>Копирование удаленной таблицы  
Чтобы выполнить копирование удаленной таблицы, используйте [создать REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) инструкции SQL. Примеры включены в разделе CREATE REMOTE TABLE.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
